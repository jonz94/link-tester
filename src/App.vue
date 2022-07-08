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
        class="block w-full rounded-md border-transparent bg-gray-100 focus:border-gray-500 focus:bg-white focus:ring-0"
        type="text"
        placeholder="Input yout link"
        v-model="link"
        ref="input"
      />
      <p class="mt-4 text-center">
        <a class="text-lg underline" :href="link" target="_blank">open {{ link }}</a>
      </p>
    </div>
  </div>
</template>
