<script>
import Sidebar from "./components/Sidebar.vue";
import Tweets from "./components/Tweets.vue";
import Rightbar from "./components/Rightbar.vue";

export default {
  name: "app",
  components: { Sidebar, Tweets, Rightbar },
};
</script>

<template>
  <div id="app" class="flex container h-screen w-full">
    <Sidebar />
    <Tweets />
    <Rightbar />
  </div>
</template>

<style scoped></style>
