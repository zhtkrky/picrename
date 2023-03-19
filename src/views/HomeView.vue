<script setup>
import { ref } from "vue";
import HeroSection from "@/components/HeroSection.vue";
const listItems = ref("");
const isDownloading = ref(false);

function dropHandler(event) {
  event.preventDefault();
  const files = event.dataTransfer.files;
  const reader = new FileReader();
  reader.readAsText(files[0]);
  reader.onload = (e) => {
    listItems.value = JSON.parse(e.target.result);
  };
}

function handleFileUpload(event) {
  const file = event.target.files[0];
  const reader = new FileReader();
  reader.readAsText(file);
  reader.onload = (e) => {
    listItems.value = JSON.parse(e.target.result);
  };
}

function downloadImage(name, url) {
  const link = document.createElement("a");
  link.setAttribute("download", name);
  fetch(url)
    .then((response) => response.blob())
    .then((blob) => {
      const url = URL.createObjectURL(blob);
      link.setAttribute("href", url);
      link.click();
      URL.revokeObjectURL(url);
    });
}

function downloadAllImages() {
  isDownloading.value = true;
  listItems.value.forEach((item, index) => {
    setTimeout(() => {
      downloadImage(item.name, item.url);
    }, 1000 * index);
    if (index === listItems.value.length - 1) {
      setTimeout(() => {
        isDownloading.value = false;
      }, 1000 * index);
    }
  });
}
</script>

<template>
  <HeroSection />

  <div id="getstarted" class="flex items-center justify-center w-full container">
    <label
      for="dropzone-file"
      @drop="dropHandler"
      @dragover.prevent
      class="flex flex-col items-center justify-center w-full h-64 border-2 border-gray-300 border-dashed rounded-lg cursor-pointer bg-gray-50 dark:hover:bg-bray-800 dark:bg-gray-700 hover:bg-gray-100 dark:border-gray-600 dark:hover:border-gray-500 dark:hover:bg-gray-600"
    >
      <div class="flex flex-col items-center justify-center pt-5 pb-6">
        <svg
          aria-hidden="true"
          class="w-10 h-10 mb-3 text-gray-400"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"
          ></path>
        </svg>
        <p class="mb-2 text-xl text-gray-500 dark:text-gray-400">
          <span class="font-semibold">Click here to upload</span>
        </p>
        <p class="text-xs text-gray-500 dark:text-gray-400">Supports only JSON files.</p>
      </div>
      <input id="dropzone-file" type="file" @change="handleFileUpload" class="hidden" />
    </label>
  </div>

  <div class="flex justify-between items-center relative w-full px-5 pt-12 mx-auto md:px-12 lg:px-20 max-w-7xl">
    <button
      class="items-center justify-center w-full px-6 py-3 text-center text-white duration-200 bg-slate-600 border-2 border-slate-600 nline-flex hover:bg-slate-700 hover:border-slate-600 rounded-xl hover:text-white focus:outline-none lg:w-auto focus-visible:outline-black focus-visible:ring-black"
      @click="downloadAllImages()"
      :disabled="isDownloading"
    >
      <span class="font-semibold">
        {{ isDownloading ? "Downloading..." : "Download All" }}
      </span>
    </button>
    <div
      class="items-center justify-center w-full px-6 py-3 text-center text-white duration-200 bg-slate-600 border-2 border-slate-600 nline-flex hover:bg-slate-700 hover:border-slate-600 rounded-xl hover:text-white focus:outline-none lg:w-auto focus-visible:outline-black focus-visible:ring-black"
    >
      <span class="font-semibold"> {{ listItems.length }} </span>
    </div>
  </div>

  <section v-if="listItems" class="flex items-center w-full">
    <div class="relative items-center w-full px-5 py-12 mx-auto md:px-12 lg:px-20 max-w-7xl">
      <div class="grid grid-cols-2 gap-6 py-12 md:grid-cols-2 lg:grid-cols-4">
        <figure v-for="item in listItems" :key="item.url">
          <img class="w-full bg-gray-200 rounded-xl" :src="item.url" :alt="item.name" width="1310" height="873" />
          <p class="mt-5 text-lg font-medium leading-6">{{ item.name }}</p>
          <div class="flex gap-3 mt-2 justify-left">
            <button
              class="inline-flex items-center justify-center text-sm font-semibold duration-200 focus:outline-none focus-visible:outline-gray-600"
              href=""
              @click="downloadImage(item.name, item.url)"
            >
              <span> Download </span>
            </button>
          </div>
        </figure>
      </div>
    </div>
  </section>
  <section v-if="!listItems" class="flex items-center w-full">
    <div class="relative items-center w-full px-5 py-4 mx-auto md:px-12 lg:px-20 max-w-7xl">
      <div class="grid grid-cols-2 gap-6 py-12 md:grid-cols-2 lg:grid-cols-4">
        <figure>
          <img
            class="w-full bg-gray-200 rounded-xl"
            src="../assets/placeholder.jpeg"
            alt="item.name"
            width="1310"
            height="873"
          />
        </figure>
        <figure>
          <img
            class="w-full bg-gray-200 rounded-xl"
            src="../assets/placeholder.jpeg"
            alt="item.name"
            width="1310"
            height="873"
          />
        </figure>
        <figure>
          <img
            class="w-full bg-gray-200 rounded-xl"
            src="../assets/placeholder.jpeg"
            alt="item.name"
            width="1310"
            height="873"
          />
        </figure>
        <figure>
          <img
            class="w-full bg-gray-200 rounded-xl"
            src="../assets/placeholder.jpeg"
            alt="item.name"
            width="1310"
            height="873"
          />
        </figure>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* ul {
  width: 100%;
  list-style: none;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

li {
  width: 300px;
  height: 400px;
  margin: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
} */
</style>
