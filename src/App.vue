<script setup lang="ts">
import { onMounted, ref } from 'vue'

const link = ref('')
const input = ref<HTMLInputElement | null>(null)

onMounted(() => input.value?.focus())
</script>

<template>
  <div class="flex min-h-screen flex-col items-center">
    <h1 class="my-8 text-2xl font-black">Link Tester</h1>
    <div>
      <input
        class="block w-full rounded-md border-transparent bg-gray-100 focus:border-gray-500 focus:bg-white focus:ring-0 sm:min-w-[28rem]"
        type="text"
        placeholder="Input your link, example: https://link-tester.jonz94.dev"
        v-model="link"
        ref="input"
      />
      <p v-if="link" class="mt-4 max-w-[100vw] space-x-2 break-all text-center text-lg">
        <span>open</span>
        <a class="underline" :href="link" target="_blank">{{ link }}</a>
      </p>
    </div>
  </div>
</template>
