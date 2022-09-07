<template>
  <div
    class="md:w-1/5 border-r border-lighter lg:px-6 px-2 py-2 flex flex-col justify-between"
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
          src="../assets/images/profile1.png"
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
            src="../assets/images/profile1.png"
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
</template>

<script>
export default {
  name: "sidebar",
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
    };
  },
};
</script>

<style></style>
