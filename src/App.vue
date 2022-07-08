<script setup lang="ts">
import { onMounted, ref } from 'vue'

const link = ref('')
const input = ref<HTMLInputElement | null>(null)

onMounted(() => input.value?.focus())

function updateLink(value: string) {
  link.value = value
}
</script>

<template>
  <div class="prose-2xl flex min-h-screen flex-col items-center">
    <h1 class="my-8 text-2xl font-black">Link Tester</h1>
    <div>
      <input
        class="input input-bordered w-full rounded-lg sm:min-w-[28rem]"
        type="text"
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
</template>
