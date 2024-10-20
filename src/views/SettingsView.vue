<template>
  <div class="w-full h-full flex-shrink flex flex-nowrap flex-col p-4 gap-4 overflow-hidden lg:flex-row">
    <div class="w-full h-full flex-shrink rounded-box bg-black flex overflow-hidden">
      <img src="/logo.jpg" alt="logo" class="max-w-full max-h-full m-auto">
    </div>
    <div class="w-full h-full flex-shrink">
      <div class="flex flex-col gap-4 mb-4">
        <span class="text-xl">Settings</span>
        <div class="flex flex-col gap-2">
          <div>
            <span>M3U File URL:</span>
            <div class="join w-full items-center">
              <div class="input input-bordered w-full flex items-center gap-2 join-item">
                <input type="text" class="grow h-full" placeholder="https://url.com/" v-model="url" />
              </div>
              <div class="indicator">
                <button class="btn join-item" :disabled="!code" @click="saveUrl">Save</button>
              </div>
            </div>
          </div>
          <div>
            <span>Easy Access Code</span>
            <div class="join w-full items-center">
              <div class="input input-bordered w-full flex items-center gap-2 join-item min-w-16">
                <input type="text" class="grow h-full min-w-0" placeholder="" v-model="code" />
              </div>
              <button class="btn join-item" @click="createAccessCode">Create</button>
              <button class="btn join-item" @click="getAccessCode">Get</button>
              <button class="btn join-item" @click="deleteAccessCode">Remove</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { ACCESSCODE, PLAYLIST } from '@/constant';
import { deleteDocument, getDocument, increaseDocument, setDocument } from '@/services/firebase/firestore';
import { encode } from '@/services/sqids';
import { useAppStore } from '@/stores/app';

export default {
  data() {
    return {
      url: "",
      code: "",
      appStore: useAppStore()
    }
  },
  methods: {
    async getIndex() {
      let index = 0;
      const indexDoc = await getDocument(ACCESSCODE, "-index")
      if (indexDoc.exists()) index = indexDoc.data().index
      return index
    },
    async saveUrl() {
      if (this.code) {
        await setDocument(ACCESSCODE, this.code, { url: this.url, timesamp: Date.now() })
      }
    },
    async createAccessCode() {
      localStorage.setItem("url", this.url)
      const code = encode(await this.getIndex())
      await setDocument(ACCESSCODE, code, { url: this.url, timesamp: Date.now() })
      await increaseDocument(ACCESSCODE, "-index", "index").catch(() => {
        return setDocument(ACCESSCODE, "-index", { index: 1 })
      })
      this.code = code
      localStorage.setItem("code", this.code)
    },
    async getAccessCode() {
      const urlRef = await getDocument(ACCESSCODE, this.code)
      if (urlRef.exists()) this.url = urlRef.data().url
    },
    async deleteAccessCode() {
      await deleteDocument(ACCESSCODE, this.code)
      localStorage.removeItem("code")
      this.code = ""
    }
  },
  async beforeMount() {
    this.appStore.overflow = true
    this.url = localStorage.getItem("url") || ""
    this.code = localStorage.getItem("code") || ""
  },
  beforeUnmount() {
    this.appStore.overflow = false
  }
}
</script>

<style>
.input:focus,
.input input:focus,
.input:focus-within {
  outline: none;
}
</style>