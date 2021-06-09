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
        <div class="w-full h-full relative overflow-y-scroll no-scrollbar">
          <!-- header -->
          <div
            class="w-full sticky top-0 px-5 py-3 z-10 flex items-center justify-between bg-black"
          >
            <div class="flex items-center">
              <button
                v-for="(btn,key) in arrowbuttons "
                :key="key"
                class="rounded-full focus:outline-none bg-black mr-2 w-9 h-9 text-white"
              >
                <i class="material-icons text-3xl">{{ btn.icon }}</i>
              </button>
            </div>
            <div class="relative">
              <button
                @click="showDropDown = !showDropDown"
                class="bg-light rounded-full p-1 focus:outline-none flex items-center"
              >
                <img
                  src="https://cdn.quasar.dev/img/boy-avatar.png"
                  alt
                  class="rounded-full h-6 w-6"
                />
                <p class="text-white font-semibold text-xs ml-1 mr-2">Punith Fury</p>
                <i v-if="showDropDown" class="material-icons text-white">arrow_drop_down</i>
                <i v-if="!showDropDown" class="material-icons text-white">arrow_drop_up</i>
              </button>
              <div
                @click="showDropDown = !showDropDown"
                v-if="!showDropDown"
                class="absolute bg-light w-full rounded mt-1"
              >
                <button
                  class="text-center focus:outline-none text-sm w-full py-2 text-lightest border-b border-lightest opacity-75 hover:opacity-100 hover:text-white"
                >Accounts</button>
                <button
                  class="text-center focus:outline-none text-sm w-full py-2 text-lightest border-b border-light hover:text-white opacity-75 hover:opacity-100"
                >Log Out</button>
              </div>
            </div>
          </div>
          <!-- body -->
          <div class="px-6 py-3">
            <div class="flex items-center justify-between">
              <h3
                class="text-white text-2xl text-semibold tracking-wide hover:underline"
              >Recently Played</h3>
              <h3 class="text-xs pr-6 text-lightest tracking-wide hover:underline">See All</h3>
            </div>
            <div class="mt-3 w-full flex flex-wrap">
              <div v-for="n in 8" :key="n" class="p-2 w-48 relative">
                <div
                  class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100"
                >
                  <div class="bg-green rounded-full px-2 h-10 flex items-center justify-end">
                    <i class="material-icons">play_arrow</i>
                  </div>
                </div>
                <div class="bg-light w-full p-5 h-auto">
                  <img src="./songp.jpg" class="h-auto w-full shadow mt-2" alt />
                  <h3 class="text-sm font-semibold tracking-wide text-white mt-3">Love the Vue</h3>
                  <h3 class="text-xs text-lightest tracking-wide">By Spotify</h3>
                </div>
              </div>
            </div>
          </div>
          <div class="px-6 py-3">
            <div>
              <h3 class="text-white text-2xl text-semibold tracking-wide">Your Recommendations</h3>
              <h3
                class="text-sm text-lightest"
              >Get better recommendations from listening to more songs</h3>
            </div>
            <div class="mt-3 w-full flex flex-wrap">
              <div v-for="n in 8" :key="n" class="p-2 w-48 relative">
                <div
                  class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100"
                >
                  <div class="bg-green rounded-full px-2 h-10 flex items-center justify-end">
                    <i class="material-icons">play_arrow</i>
                  </div>
                </div>
                <div class="bg-light w-full p-5 h-auto">
                  <img src="./songp.jpg" class="h-auto w-full shadow mt-2" alt />
                  <h3 class="text-sm font-semibold tracking-wide text-white mt-3">Love the Vue</h3>
                  <h3 class="text-xs text-lightest tracking-wide">By Spotify</h3>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- play Bar -->
      <div
        class="w-full p-5 h-100 bg-light flex justify-between px-3 border-t border-dark"
        style="height: 12vh;"
      >
        <div class="flex h-full items-center">
          <div>
            <h1 class="text-sm text-white tracking-wide mb-1">Summer in the city - remastered</h1>
            <h2 class="text-xs text-lightest tracking-wide">The Loving Spoonful</h2>
          </div>
          <i class="material-icons text-base text-green mx-4">favorite</i>
          <i class="material-icons text-base text-lightest hover:text-white">picture_in_picture</i>
        </div>
        <div class="flex flex-col justify-center w-1/3 items-center">
          <div class="flex items-center">
            <button class="mx-5 text-lightest focus:outline-none hover:text-white">
              <i class="text-lg material-icons">shuffle</i>
            </button>
            <button class="text-lightest focus:outline-none hover:text-white">
              <i class="text-lg material-icons">skip_previous</i>
            </button>
            <button
              @click.prevent="playsong('song.mp3')"
              class="rounded-full focus:outline-none flex items-center mx-5 justify-center h-8 w-8 border-lightest border text-lightest hover:text-white"
            >
              <i v-if="play" class="material-icons">play_arrow</i>
              <i v-else class="material-icons">pause</i>
            </button>
            <button class="text-lightest focus:outline-none hover:text-white">
              <i class="text-lg material-icons">skip_next</i>
            </button>
            <button class="mx-5 focus:outline-none text-lightest hover:text-white">
              <i class="text-lg material-icons">repeat</i>
            </button>
          </div>
          <div class="w-full flex items-center">
            <p class="text-white text-xs mt-5 mr-2">0:27</p>
            <div class="h-1 w-full bg-lightest rounded-full mt-5 flex items-center">
              <div class="h-full w-2/4 bg-green"></div>
              <div class="w-3 h-3 rounded-full bg-white shadow"></div>
            </div>
            <p class="text-lightest text-xs mt-5 ml-2">1:27</p>
          </div>
        </div>
        <div class="flex items-center">
          <i class="material-icons text-2xl text-lightest">playlist_play</i>
          <i class="material-icons text-base text-lightest mx-3">important_devices</i>
          <i class="material-icons text-lg text-lightest mr-2">volume_up</i>
          <div class="w-20 h-1 bg-lightest rounded-full flex items-center">
            <div class="h-full w-1/4 bg-white"></div>
            <div class="w-3 h-3 rounded-full bg-white shadow"></div>
          </div>
        </div>
      </div>
    </div>
    <div class="bg-dark h-screen block md:hidden">
      <div
        class="flex w-full h-full justify-center items-center text-lg text-white"
      >Not Support for Mobile</div>
    </div>
  </div>
</template>


<style>
</style>



<script>
export default {
  data() {
    return {
      setID: "home",
      showDropDown: true,
      play: true,
      count: 0,
      audio: null,
      pages: [
        { id: "home", name: "Home", icon: "home" },
        { id: "search", name: "Search", icon: "search" },
        { id: "Library", name: "Your Library", icon: "bar_chart" },
      ],
      playlistbuttons: [
        { id: "1", name: "Create Playlist", icon: "add" },
        { id: "2", name: "Liked Songs", icon: "favorite" },
      ],
      albums: [
        { name: "drive" },
        { name: "drive2" },
        { name: "driv3" },
        { name: "drive4" },
        { name: "drive5" },
        { name: "drive6" },
      ],
      arrowbuttons: [
        { icon: "keyboard_arrow_left" },
        { icon: "keyboard_arrow_right" },
      ],
    };
  },
  methods: {
    playsong(song) {
      if (song) {
        if (this.count == 0) {
          this.audio = new Audio(song);
          this.count = 100;
          this.audio.play();
        } else {
          if (this.play) {
            this.audio.play();
          } else {
            this.audio.pause();
          }
        }
      }
      this.play = !this.play;
    },
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