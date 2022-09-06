<script>
import elomImg from "./assets/images/elon.jpg";
import monkImg from "./assets/images/monk.jpg";
import kevinImg from "./assets/images/kevin.jpg";

export default {
  name: "app",
  components: {},
  data() {
    return {
      tabs: [
        { icon: "fas fa-home", title: "Home", id: "home" },
        { icon: "fas fa-hashtag", title: "Explore", id: "explore" },
        { icon: "far fa-bell", title: "Notifications", id: "notifications" },
        { icon: "far fa-envelope", title: "Messages", id: "messages" },
        { icon: "far fa-bookmark", title: "Bookmark", id: "bookmark" },
        { icon: "fas fa-clipboard-list", title: "Lists", id: "lists" },
        { icon: "far fa-user", title: "Profile", id: "profile" },
        { icon: "fas fa-ellipsis-h", title: "More", id: "more" },
      ],
      id: "home",
      dropdown: false,
      trending: [
        {
          top: "Trending in TX",
          title: "Gigi",
          bottom: "Trending with: Rip Gigi",
        },
        { top: "Music", title: "We Won", bottom: "135K Tweets" },
        { top: "Pop", title: "Blue Ivy", bottom: "49k Tweets" },
        { top: "Trending in US", title: "Denim Day", bottom: "35k Tweets" },
        { top: "Trending", title: "When Beyonce", bottom: "20.5k Tweets" },
      ],
      friends: [
        {
          src: elomImg,
          name: "Elon Musk",
          handle: "@teslaBoy",
        },
        {
          src: monkImg,
          name: "Adrian Monk",
          handle: "@detective:)",
        },
        {
          src: kevinImg,
          name: "Kevin Hart",
          handle: "@miniRock",
        },
      ],
    };
  },
};
</script>

<template>
  <div id="app" class="flex container h-screen w-full">
    <!-- side nav -->
    <div
      class="lg:w-1/5 border-r border-lighter lg:px-6 px-2 py-2 flex flex-col justify-between"
    >
      <div class="">
        <button
          class="h-12 w-12 hover:bg-lightblue text-3xl text-blue rounded-full"
        >
          <i class="fab fa-twitter"></i>
        </button>
        <div>
          <button
            v-for="(tab, i) in tabs"
            :key="i"
            @click="id = tab.id"
            :class="`flex items-center py-2 px-4 hover:bg-lightblue hover:text-blue rounded-full mr-auto mb-3 focus:outline-none ${
              id === tab.id ? 'text-blue' : ''
            }`"
          >
            <i :class="`${tab.icon} text-2xl mr-4 text-left`"></i>
            <p class="text-lg font-semibold text-left hidden lg:block">
              {{ tab.title }}
            </p>
          </button>
        </div>
        <button
          class="text-white bg-blue rounded-full font-semibold w-12 h-12 lg:w-full lg:h-auto p-3 focus:outline-none hover:bg-darkblue"
        >
          <p class="hidden lg:block">Tweet</p>
          <i class="fas fa-plus lg:hidden"></i>
        </button>
      </div>
      <div class="lg:w-full relative">
        <button
          @click="dropdown = true"
          class="flex items-center w-full hover:bg-lightblue rounded-full focus:outline-none"
        >
          <img
            src="./assets/images/profile1.png"
            class="w-10 h-10 rounded-full border-lighter"
          />
          <div class="hidden lg:block ml-4">
            <p class="text-sm font-bold leading-tight">xXx sniper</p>
            <p class="text-sm leading-tight">@sniper</p>
          </div>
          <i class="fas fa-angle-down ml-auto text-lg"></i>
        </button>
        <div
          v-if="dropdown === true"
          class="hidden lg:block absolute bottom-0 left-0 mb-16 w-64 rounded-lg shadow-md border-lightest bg-white"
        >
          <button
            @click="dropdown = false"
            class="flex items-center w-full hover:bg-lightest p-3 focus:outline-none"
          >
            <img
              src="./assets/images/profile1.png"
              class="w-10 h-10 rounded-full border-lighter"
            />
            <div class="ml-4">
              <p class="text-sm font-bold leading-tight">xXx sniper</p>
              <p class="text-sm leading-tight">@sniper</p>
            </div>
            <i class="fas fa-check ml-auto text-blue"></i>
          </button>
          <button
            @click="dropdown = false"
            class="w-full text-left hover:bg-lightest border-t border-lighter p-3 text-sm focus:outline-none"
          >
            Add an existing account
          </button>
          <button
            @click="dropdown = false"
            class="w-full text-left hover:bg-lightest border-t border-lighter p-3 text-sm focus:outline-none"
          >
            Log out @sniper
          </button>
        </div>
      </div>
    </div>
    <!-- tweets  -->
    <div class="w-1/2 h-full"></div>
    <!-- trending -->
    <div
      class="md:block hidden w-1/3 h-full border-l border-lighter py-2 px-6 overflow-y-scroll relative"
    >
      <input
        type="text"
        class="pl-12 rounded-full w-full p-2 bg-lighter text-sm"
        placeholder="Search Twitter"
      />
      <i
        class="fas fa-search absolute left-0 top-0 mt-4 ml-12 text-sm text-light"
      ></i>
      <div class="w-full rounded-lg bg-lightest my-4">
        <div class="flex items-center justify-between p-3">
          <p class="text-lg font-bold">Trends for You</p>
          <i class="fas fa-cog text-lg text-blue"></i>
        </div>
        <button
          v-for="(trend, i) in trending"
          :key="i"
          class="w-full flex justify-between hover:bg-lighter p-3 border-t border-lighter"
        >
          <div>
            <p class="text-sm text-left leading-tight text-dark">
              {{ trend.top }}
            </p>
            <p class="font-bold text-left leading-tight">{{ trend.title }}</p>
            <p class="text-left leading-tight text-dark">{{ trend.bottom }}</p>
          </div>
          <i class="fas fa-angle-down text-lg text-dark"></i>
        </button>
        <button
          class="p-3 w-full hover:bg-lighter text-left border-t border-lighter text-blue"
        >
          Show More
        </button>
      </div>
      <div class="w-full rounded-lg bg-lightest my-4">
        <div class="p-3">
          <p class="text-lg font-bold">Who to follow</p>
        </div>
        <button
          v-for="(celeb, i) in friends"
          :key="i"
          class="w-full flex hover:bg-lighter p-3 border-t border-lighter"
        >
          <img
            :src="`${celeb.src}`"
            class="w-12 h-12 rounded-full border-lighter"
          />
          <div class="hidden lg:block ml-4">
            <p class="text-sm font-bold leading-tight">{{ celeb.name }}</p>
            <p class="text-sm leading-tight">{{ celeb.handle }}</p>
          </div>
          <button
            class="ml-auto text-sm text-blue py-1 px-4 rounded-full border-2 border-blue"
          >
            Follow
          </button>
        </button>
        <button
          class="p-3 w-full hover:bg-lighter text-left border-t border-lighter text-blue"
        >
          Show More
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
