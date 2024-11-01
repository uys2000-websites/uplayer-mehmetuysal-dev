<template>
  <div class="h-screen w-full -mt-[80px] overflow-auto">
    <div class="hero bg-base-200 min-h-screen">
      <div class="hero-content flex-col lg:flex-row w-full justify-around">
        <img src="/images/watch.jpeg" class="max-w-xs rounded-lg shadow-2xl" />
        <div>
          <h1 class="text-5xl font-bold">Free</h1>
          <h2 class="text-2xl">Web Based IP TV Application</h2>
        </div>
      </div>
    </div>
    <div class="hero bg-base-300 min-h-screen">
      <div class="hero-content flex-col lg:flex-row-reverse w-full justify-around">
        <img src="/images/bridge.jpeg" class="max-w-xs rounded-lg shadow-2xl" />
        <div>
          <h1 class="text-5xl font-bold">Download Now</h1>
          <p class="py-6">
            Available for Android, Windows and Linux.<br>
            Latest version available on github.
          </p>
          <div class="flex flex-col">
            <a class="btn btn-ghost"
              href="https://play.google.com/store/apps/details?id=com.uys2000.uplayer&pcampaignid=web_share"
              target="_blank">
              <img src="/images/play-store.png" class="w-8" />
              Download For Android</a>
            <a class="btn btn-ghost" href="https://snapcraft.io/uplayer" target="_blank">
              <img src="/images/snapcraft.png" class="w-8" />
              Download For Linux</a>
            <a class="btn btn-ghost" href="https://github.com/uys2000-projects/uplayer-mehmetuysal-dev-desktop/releases"
              target="_blank">
              <img src="/images/microsoft-store.png" class="w-8" />
              Download For Window</a>
          </div>
        </div>
      </div>
    </div>
    <div class="hero min-h-screen bg-fixed" style="background-image: url(/images/code.webp);">
      <div class="hero-overlay bg-opacity-60"></div>
      <div class="hero-content text-neutral-content text-center">
        <div class="max-w-md bg-neutral text-neutral-content p-8 rounded-box bg-opacity-90">
          <h1 class="text-5xl font-bold">Contact With Me</h1>
          <div class="py-6 flex flex-col gap-2 links">
            <span>
              <a class="link" href="mailto:hi@mehmetuysal.dev" target="_blank">hi@mehmetuysal.dev</a>
            </span>
            <span>
              <a class="link" href="https://mehmetuysal.dev" target="_blank">mehmetuysal.dev</a>
            </span>
            <div class="mt-4 flex flex-col">
              Source Codes
              <div>
                <a class="link mx-1" href="https://github.com/uys2000-websites/uplayer-mehmetuysal-dev"
                  target="_blank">Web Site</a>
                <a class="link mx-1" href="https://github.com/uys2000-projects/uplayer-mehmetuysal-dev"
                  target="_blank">Android</a>
                <a class="link mx-1" href="https://github.com/uys2000-projects/uplayer-mehmetuysal-dev-desktop"
                  target="_blank">Windows/Linux</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">

export default {
  data() {
    return {}
  }
}
</script>
