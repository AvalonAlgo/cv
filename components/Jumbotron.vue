<script setup lang="ts">
  const items = [
    "https://picsum.photos/1920/1080?random=1",
    "https://picsum.photos/1920/1080?random=2",
    "https://picsum.photos/1920/1080?random=3",
    "https://picsum.photos/1920/1080?random=4",
    "https://picsum.photos/1920/1080?random=5",
    "https://picsum.photos/1920/1080?random=6",
  ];

  const carouselRef = ref();

  onMounted(() => {
    setInterval(() => {
      if (!carouselRef.value) return;

      if (carouselRef.value.page === carouselRef.value.pages) {
        return carouselRef.value.select(0);
      }

      carouselRef.value.next();
    }, 3000);
  });
</script>

<style scoped>
  @keyframes rgb-color-cycle {
    0% {
      color: #7b68ee; /* Medium Slate Blue */
      text-shadow: 0 0 8px #7b68ee;
    }
    25% {
      color: #6a5acd; /* Slate Blue */
      text-shadow: 0 0 8px #6a5acd;
    }
    50% {
      color: #48d1cc; /* Medium Turquoise */
      text-shadow: 0 0 8px #48d1cc;
    }
    75% {
      color: #20b2aa; /* Light Sea Green */
      text-shadow: 0 0 8px #20b2aa;
    }
    100% {
      color: #7b68ee; /* Medium Slate Blue */
      text-shadow: 0 0 8px #7b68ee;
    }
  }

  .rgb-cycle {
    animation: rgb-color-cycle 4s linear infinite;
  }
</style>

<template>
  <div class="text-gray-400 bg-gray-900 body-font">
    <div
      class="container mx-auto flex px-4 py-24 sm:flex-row flex-col items-center"
    >
      <div
        class="lg:flex-grow md:w-1/2 lg:pr-24 md:pr-16 flex flex-col md:items-start md:text-left mb-16 md:mb-0 items-center text-center"
      >
        <h1
          class="title-font sm:text-5xl text-4xl mb-4 font-medium text-white subpixel-antialiased"
        >
          Welcome to my <span class="rgb-cycle">homepage</span>!
        </h1>
      </div>
      <UCarousel
        ref="carouselRef"
        v-slot="{ item }"
        :items="items"
        :ui="{ item: 'basis-full' }"
        class="rounded-lg overflow-hidden w-full"
        indicators
      >
        <img :src="item" class="w-full" draggable="false" />
      </UCarousel>
    </div>
    <div class="container px-4 py-24 mx-auto">
      <div class="xl:w-1/2 lg:w-3/4 w-full mx-auto text-center">
        <p class="leading-relaxed text-2xl subpixel-antialiased">
          All we have to decide is what to do with the time that is given to us.
        </p>
        <span class="inline-block h-1 w-10 rounded bg-indigo-500 mt-4 mb-3" />
        <h2
          class="text-white font-medium title-font tracking-wider text-sm subpixel-antialiased"
        >
          Gandalf the Grey
        </h2>
        <NuxtImg src="/wizard.gif" class="mx-auto mt-3" />
      </div>
    </div>
  </div>
</template>
