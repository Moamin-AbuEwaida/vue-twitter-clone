<template>
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
</template>

<script>
import elomImg from "../assets/images/elon.jpg";
import monkImg from "../assets/images/monk.jpg";
import kevinImg from "../assets/images/kevin.jpg";
export default {
  name: "Rightbar",
  data() {
    return {
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

<style></style>
