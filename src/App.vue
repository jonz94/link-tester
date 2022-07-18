<script setup lang="ts">
import { onMounted, ref } from 'vue'

const isDrawerOpened = ref(false)
const link = ref('')
const input = ref<HTMLInputElement | null>(null)

onMounted(() => input.value?.focus())

function toggleDrawer() {
  isDrawerOpened.value = !isDrawerOpened.value
}

function updateLink(value: string) {
  link.value = value
}
</script>

<template>
  <div class="drawer drawer-end">
    <input type="checkbox" class="drawer-toggle" v-model="isDrawerOpened" />

    <div class="drawer-content">
      <div class="prose-2xl flex min-h-screen flex-col items-center">
        <h1 class="my-8 text-2xl font-black">Link Tester</h1>
        <div>
          <input
            class="input input-bordered w-full rounded-lg sm:min-w-[28rem]"
            type="url"
            placeholder="Input your link, example: https://link-tester.jonz94.dev"
            :value="link"
            v-on:keyup="(event) => updateLink((event.target as HTMLInputElement).value)"
            v-on:compositionend="(event) => updateLink(event.data)"
            ref="input"
          />
          <p v-if="link" class="mt-4 max-w-[100vw] space-x-2 break-all text-center text-lg">
            <span>open</span>
            <a class="link" :href="link" target="_blank">{{ link }}</a>
          </p>
        </div>
      </div>
    </div>

    <div class="drawer-side">
      <label for="drawer" class="drawer-overlay"></label>
      <ul class="menu w-80 bg-base-100 px-4 pt-16 pb-4 text-base-content [&>li>a]:rounded">
        <li>
          <a>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 stroke-current" viewBox="0 0 512 512">
              <title>Sunny</title>
              <path
                fill="none"
                stroke-linecap="round"
                stroke-miterlimit="10"
                stroke-width="32"
                d="M256 48v48M256 416v48M403.08 108.92l-33.94 33.94M142.86 369.14l-33.94 33.94M464 256h-48M96 256H48M403.08 403.08l-33.94-33.94M142.86 142.86l-33.94-33.94"
              />
              <circle
                cx="256"
                cy="256"
                r="80"
                fill="none"
                stroke-linecap="round"
                stroke-miterlimit="10"
                stroke-width="32"
              />
            </svg>
            <span>Light / Dark Mode (TODO)</span>
          </a>
        </li>
        <li>
          <a>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 fill-current stroke-current" viewBox="0 0 512 512">
              <rect x="336" y="336" width="80" height="80" rx="8" ry="8" />
              <rect x="272" y="272" width="64" height="64" rx="8" ry="8" />
              <rect x="416" y="416" width="64" height="64" rx="8" ry="8" />
              <rect x="432" y="272" width="48" height="48" rx="8" ry="8" />
              <rect x="272" y="432" width="48" height="48" rx="8" ry="8" />
              <rect x="336" y="96" width="80" height="80" rx="8" ry="8" />
              <rect
                x="288"
                y="48"
                width="176"
                height="176"
                rx="16"
                ry="16"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="32"
              />
              <rect x="96" y="96" width="80" height="80" rx="8" ry="8" />
              <rect
                x="48"
                y="48"
                width="176"
                height="176"
                rx="16"
                ry="16"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="32"
              />
              <rect x="96" y="336" width="80" height="80" rx="8" ry="8" />
              <rect
                x="48"
                y="288"
                width="176"
                height="176"
                rx="16"
                ry="16"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="32"
              />
            </svg>
            <span>QRCode (TODO)</span>
          </a>
        </li>
        <li class="mt-auto">
          <a href="https://github.com/jonz94/link-tester" target="_blank">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 fill-current" viewBox="0 0 512 512">
              <path
                d="M256 32C132.3 32 32 134.9 32 261.7c0 101.5 64.2 187.5 153.2 217.9a17.56 17.56 0 003.8.4c8.3 0 11.5-6.1 11.5-11.4 0-5.5-.2-19.9-.3-39.1a102.4 102.4 0 01-22.6 2.7c-43.1 0-52.9-33.5-52.9-33.5-10.2-26.5-24.9-33.6-24.9-33.6-19.5-13.7-.1-14.1 1.4-14.1h.1c22.5 2 34.3 23.8 34.3 23.8 11.2 19.6 26.2 25.1 39.6 25.1a63 63 0 0025.6-6c2-14.8 7.8-24.9 14.2-30.7-49.7-5.8-102-25.5-102-113.5 0-25.1 8.7-45.6 23-61.6-2.3-5.8-10-29.2 2.2-60.8a18.64 18.64 0 015-.5c8.1 0 26.4 3.1 56.6 24.1a208.21 208.21 0 01112.2 0c30.2-21 48.5-24.1 56.6-24.1a18.64 18.64 0 015 .5c12.2 31.6 4.5 55 2.2 60.8 14.3 16.1 23 36.6 23 61.6 0 88.2-52.4 107.6-102.3 113.3 8 7.1 15.2 21.1 15.2 42.5 0 30.7-.3 55.5-.3 63 0 5.4 3.1 11.5 11.4 11.5a19.35 19.35 0 004-.4C415.9 449.2 480 363.1 480 261.7 480 134.9 379.7 32 256 32z"
              />
            </svg>
            <span>Source Code</span>
          </a>
        </li>
      </ul>
    </div>

    <div class="fixed top-4 right-4 z-20">
      <label
        class="btn swap btn-ghost btn-circle swap-rotate h-10 min-h-0 w-10"
        :class="isDrawerOpened ? 'swap-active' : ''"
        @click="toggleDrawer"
      >
        <svg xmlns="http://www.w3.org/2000/svg" class="swap-off h-6 w-6 stroke-current" viewBox="0 0 512 512">
          <path
            fill="none"
            stroke-linecap="round"
            stroke-miterlimit="10"
            stroke-width="32"
            d="M80 160h352M80 256h352M80 352h352"
          />
        </svg>

        <svg xmlns="http://www.w3.org/2000/svg" class="swap-on h-6 w-6 stroke-current" viewBox="0 0 512 512">
          <path
            fill="none"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="32"
            d="M368 368L144 144M368 144L144 368"
          />
        </svg>
      </label>
    </div>
  </div>
</template>
