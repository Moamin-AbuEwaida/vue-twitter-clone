<template>
  <div class="h-full overflow-y-scroll">
    <div
      class="px-5 py-3 border-b border-lighter flex items-center justify-between"
    >
      <h1 class="text-lg font-bold">Home</h1>
      <i class="far fa-star text-xl text-blue"></i>
    </div>
    <div class="px-5 py-3 border-b-8 border-lighter flex">
      <div class="flex-none">
        <img
          src="../assets/images/profile1.png"
          alt=""
          class="flex-none w-12 h-12 rounded-full border border-lighter"
        />
      </div>
      <form v-on:submit.prevent="addNewTweet" class="w-full px-4 relative">
        <textarea
          v-model="tweet.content"
          placeholder="What's up?"
          class="w-full focus:outline-none mt-3 pb-3"
        ></textarea>
        <div class="hidden md:block items-center">
          <i class="text-lg text-blue mr-4 far fa-image"></i>
          <i class="text-lg text-blue mr-4 fas fa-file"></i>
          <i class="text-lg text-blue mr-4 far fa-chart-bar"></i>
          <i class="text-lg text-blue mr-4 far fa-smile"></i>
        </div>
        <button
          type="submit"
          class="md:h-10 md:w-auto h-10 w-10 px-4 flex items-center justify-center text-white font-semibold bg-blue hover:bg-darkblue focus:outline-none rounded-full absolute bottom-0 right-0"
        >
          <p class="hidden lg:block">Tweet</p>
          <i class="fas fa-plus lg:hidden"></i>
        </button>
      </form>
    </div>
    <div class="flex flex-col-reverse">
      <div
        v-for="(tweet, i) in tweets"
        :key="i"
        class="w-full p-4 border-b hover:bg-lighter flex"
      >
        <div class="flex-none mr-4">
          <img
            src="../assets/images/profile1.png"
            class="h-12 w-12 rounded-full flex-none"
          />
        </div>
        <div class="w-full">
          <div class="flex items-center w-full">
            <p class="font-semibold">Steph Dietz</p>
            <p class="text-sm text-dark ml-2">@SaaSyEth</p>
            <p class="text-sm text-dark ml-2">1 sec</p>
            <i class="fas fa-angle-down text-dark ml-auto"></i>
          </div>
          <p class="py-2">
            {{ tweet.content }}
          </p>
          <div class="flex items-center justify-between w-full">
            <div class="flex items-center text-sm text-dark">
              <i class="far fa-comment mr-3"></i>
              <p>0</p>
            </div>
            <div class="flex items-center text-sm text-dark">
              <i class="fas fa-retweet mr-3"></i>
              <p>0</p>
            </div>
            <div class="flex items-center text-sm text-dark">
              <i class="fas fa-heart mr-3"></i>
              <p>1</p>
            </div>
            <div class="flex items-center text-sm text-dark">
              <i class="fas fa-share-square mr-3"></i>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div
      v-for="(follow, i) in following"
      :key="i"
      class="w-full md:w-full p-4 border-b hover:bg-lighter flex"
    >
      <div class="flex-none mr-4">
        <img :src="`${follow.src}`" class="w-12 h-12 rounded-full flex-none" />
      </div>
      <div class="w-full">
        <div class="flex items-center w-full">
          <p class="font-semibold">{{ follow.name }}</p>
          <p class="text-sm text-dark ml-2">{{ follow.handle }}</p>
          <p class="text-sm text-dark ml-2">{{ follow.time }}</p>
          <i class="fas fa-angle-down text-dark ml-auto"></i>
        </div>
        <p class="py-2">{{ follow.tweet }}</p>
        <div class="flex items-center md:justify-between w-full">
          <div class="flex items-center mr-2 text-sm text-dark">
            <i class="far fa-comment mr-1 md:mr-3"></i>
            <p>{{ follow.comments }}</p>
          </div>
          <div class="flex items-center mr-2 text-sm text-dark">
            <i class="fas fa-retweet mr-1 md:mr-3"></i>
            <p>{{ follow.retweets }}</p>
          </div>
          <div class="flex items-center mr-2 text-sm text-dark">
            <i class="fas fa-heart mr-1 md:mr-3"></i>
            <p>{{ follow.like }}</p>
          </div>
          <div class="flex items-center mr-2 text-sm text-dark">
            <i class="fas fa-share-square md:mr-3"></i>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import elomImg from "../assets/images/elon.jpg";
import monkImg from "../assets/images/monk.jpg";
import kevinImg from "../assets/images/kevin.jpg";
export default {
  name: "tweets",
  data() {
    return {
      following: [
        {
          src: elomImg,
          name: "Elon Musk",
          handle: "@teslaBoy",
          time: "20 min",
          tweet: "Should I just quarantine on mars??",
          comments: "1,000",
          retweets: "550",
          like: "1,000,003",
        },
        {
          src: kevinImg,
          name: "Kevin Hart",
          handle: "@miniRock",
          time: "55 min",
          tweet: "Should me and the rock do another sub-par movie together????",
          comments: "2,030",
          retweets: "50",
          like: "20,003",
        },
        {
          src: monkImg,
          name: "Adrian Monk",
          handle: "@detective:)",
          time: "1.4 hr",
          tweet: "say NO to toxic ppl",
          comments: "100,000",
          retweets: "1,000,002",
          like: "5,000,003",
        },
        {
          src: elomImg,
          name: "Elon Musk",
          handle: "@teslaBoy",
          time: "1.4 hr",
          tweet: "Haha just made a flame thrower. Shld I sell them?",
          comments: "100,000",
          retweets: "1,000,002",
          like: "5,000,003",
        },
        {
          src: elomImg,
          name: "Elon Musk",
          handle: "@teslaBoy",
          time: "1.4 hr",
          tweet: "Just did something crazyyyyyyy",
          comments: "100,500",
          retweets: "1,000,032",
          like: "5,000,103",
        },
      ],
      tweets: [{ content: "It's a nice weather today" }],
      tweet: { content: "" },
    };
  },
  methods: {
    addNewTweet() {
      let newTweet = {
        content: this.tweet.content,
      };
      this.tweets.push(newTweet);
    },
  },
};
</script>

<style></style>
