<script setup>
import { ref } from "vue";

const watchVideo = ref(false);
</script>

<template>
  <section>
    <div
      v-if="watchVideo"
      @click.away="watchVideo = false"
      class="relative z-10"
      aria-labelledby="modal-title"
      role="dialog"
      aria-modal="true"
    >
      <div class="fixed inset-0 bg-slate-900 bg-opacity-75 transition-opacity"></div>

      <div class="fixed inset-0 z-10 overflow-y-auto">
        <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
          <div
            class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg"
          >
            <div class="sm:flex sm:items-start">
              <video src="../assets/how-to.mp4" muted controls></video>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="relative items-center w-full px-5 py-24 mx-auto md:px-12 lg:px-16 max-w-7xl">
      <div class="relative flex-col items-center m-auto align-middle">
        <div class="grid grid-cols-1 gap-6 lg:grid-cols-2 lg:gap-24">
          <div class="relative items-center gap-12 m-auto lg:inline-flex md:order-first">
            <div class="max-w-xl text-center lg:text-left">
              <div>
                <p class="text-2xl font-medium tracking-tighter sm:text-4xl">
                  PicRename - Change the Way You Name Your Images
                </p>
                <p class="max-w-xl mt-4 text-base tracking-tight">
                  PicRename is the ultimate app for renaming your images with ease. With its intuitive interface and
                  powerful tools, you can quickly and easily change the names of your images to make them more organized
                  and easier to find. No more scrolling through endless lists of unnamed files!
                </p>
              </div>
              <div class="flex flex-col gap-3 mt-10 sm:flex-row">
                <a
                  href="#getstarted"
                  class="items-center justify-center w-full px-6 py-3 text-center text-white duration-200 bg-slate-600 border-2 border-slate-600 nline-flex hover:bg-slate-700 hover:border-slate-600 rounded-xl hover:text-white focus:outline-none lg:w-auto focus-visible:outline-black focus-visible:ring-black"
                >
                  Get started
                </a>
                <button @click="watchVideo = true" class="flex text-sm font-semibold leading-6 pt-4">
                  <svg
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                    class="mr-1"
                  >
                    <path
                      d="M14.7519 11.1679L11.5547 9.03647C10.8901 8.59343 10 9.06982 10 9.86852V14.1315C10 14.9302 10.8901 15.4066 11.5547 14.9635L14.7519 12.8321C15.3457 12.4362 15.3457 11.5638 14.7519 11.1679Z"
                      stroke="currentColor"
                      stroke-width="1"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M21 12C21 16.9706 16.9706 21 12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12Z"
                      stroke="currentColor"
                      stroke-width="1"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                  Watch the video
                </button>
              </div>
            </div>
          </div>
          <div
            class="order-first relative items-center m-auto lg:inline-flex md:order-first block w-full mt-12 aspect-square lg:mt-0 sm:hidden"
          >
            <img
              class="object-cover object-center w-full mx-auto bg-gray-300 lg:ml-auto rounded-xl"
              alt="hero"
              src="../assets/carbon.png"
            />
          </div>
        </div>
      </div>
      <div>
        <div class="pt-12 mx-auto lg:max-w-7xl">
          <dl class="grid grid-cols-1 gap-6 space-y-0 text-center lg:gap-24 lg:grid-cols-3 lg:text-left">
            <div>
              <div>
                <p class="mt-5 text-lg font-semibold leading-6">1. Convert your files to Json</p>
              </div>
              <div class="mt-2 text-base">
                To use this app you need to convert your files to Json. You can do this by using the
                <a
                  class="font-semibold text-slate-600 hover:text-slate-700 dark:text-slate-50 dark:hover:text-slate-100"
                  href="https://products.aspose.app/cells/conversion/"
                  target="_blank"
                  rel="noopener noreferrer"
                  >Aspose App</a
                >.
              </div>
            </div>
            <div>
              <div>
                <p class="mt-5 text-lg font-semibold leading-6">2. Add Google Chrome Extension</p>
              </div>
              <div class="mt-2 text-base">
                To use this app you need to add the Google Chrome Extension. You can do this by using the
                <a
                  class="font-semibold text-slate-600 hover:text-slate-700 dark:text-slate-50 dark:hover:text-slate-100"
                  href="https://chrome.google.com/webstore/detail/cors-unblock/lfhmikememgdcahcdlaciloancbhjino?hl=en"
                  target="_blank"
                  rel="noopener noreferrer"
                  >CORS Unblock</a
                >.
              </div>
            </div>
            <div>
              <div>
                <p class="mt-5 text-lg font-semibold leading-6">3. Upload your JSON file</p>
              </div>
              <div class="mt-2 text-base">
                Now you can upload your JSON file and download your renamed images. You can also download example JSON
                file
                <a
                  class="font-semibold text-slate-600 hover:text-slate-700 dark:text-slate-50 dark:hover:text-slate-100"
                  href="/public/files/example.json"
                  download
                  >here</a
                >
              </div>
            </div>
          </dl>
        </div>
      </div>
    </div>
  </section>
</template>
