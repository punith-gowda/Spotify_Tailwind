<template>
  <div>
    <div class="bg-dark h-screen md:block hidden">
      <div class="flex" style="height: 88vh;">
        <!-- side nav -->
        <div class="w-56 bg-black h-full flex-none">
          <div class="p-6">
            <img class="h-10" src="./spotifylogo.png" alt />
          </div>
          <div class="mx-2">
            <div>
              <button
                v-for="page in pages"
                @click="setID = page.id"
                :key="page.id"
                :class="`w-full focus:outline-none text-sm font-semibold rounded px-3 py-2 flex items-center justify-start ${ setID === page.id ? 'bg-light text-white': 'text-lightest' }`"
              >
                <i class="material-icons mr-3">{{ page.icon }}</i>
                <p>{{ page.name }}</p>
              </button>
            </div>
            <div class="mx-3 mt-5">
              <h3 class="text-xs text-lightest tracking-widest uppercase">Playlists</h3>
              <button
                v-for="btn in playlistbuttons"
                :key="btn.id"
                class="flex justify-start mt-3 opacity-75 hover:opacity-100 focus:outline-none"
              >
                <i class="material-icons mr-3 h-8 w-8 bg-white">{{ btn.icon }}</i>
                <p class="text-sm text-white font-semibold">{{ btn.name }}</p>
              </button>
            </div>
            <div class="mx-3">
              <div class="w-full h-10 no-scrollbar mt-2 overflow-y-scroll">
                <p
                  v-for="(album ,key) in albums"
                  :key="key"
                  class="text-lightest hover:text-white text-md py-1"
                >{{ album.name }}</p>
              </div>
              <button
                class="flex text-white justify-start mt-3 opacity-75 hover:opacity-100 focus:outline-none"
              >
                <i
                  class="material-icons mr-3 rounded-full border border-lightest text-md p-1"
                >download</i>
                <p class="pt-1">Install App</p>
              </button>
            </div>
          </div>
          <div class="relative mt-6 pt-16">
            <div
              class="p-2 w-full flex justify-end items-start h-full absolute opacity-0 hover:opacity-100"
            >
              <div class="bg-black rounded-full h-6 w-6">
                <i class="material-icons text-white">keyboard_arrow_down</i>
              </div>
            </div>
            <img class="md:block hidden" src="./songp.jpg" alt />
          </div>
        </div>

        <!-- main content -->
        <div class="w-full h-full relative bg-blue-400">
          <!-- header -->
          <div class="w-full sticky top-0 p-2"></div>
        </div>
      </div>
      <!-- play Bar -->
      <div class="w-full bg-light" style="height: 12h;"></div>
    </div>
    <div class="bg-dark h-screen block md:hidden">
      <div
        class="flex w-full h-full justify-center items-center text-lg text-white"
      >Not Support for Mobile</div>
    </div>
  </div>
</template>

<script setup>
</script>

<style>
</style>



<script>
export default {
  data() {
    return {
      pages: [
        { id: "home", name: "Home", icon: "home" },
        { id: "search", name: "Search", icon: "search" },
        { id: "Library", name: "Your Library", icon: "bar_chart" },
      ],
      playlistbuttons: [
        { id: "1", name: "Create Playlist", icon: "add" },
        { id: "2", name: "Liked Songs", icon: "favorite" },
      ],
      setID: "home",
      albums: [
        { name: "drive" },
        { name: "drive2" },
        { name: "driv3" },
        { name: "drive4" },
        { name: "drive5" },
        { name: "drive6" },
      ],
    };
  },
};
</script>

<style>
.no-scrollbar::-webkit-scrollbar {
  display: none;
}

.no-scrollbar {
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}
</style>