<template>
  <div>
    <div class="flex justify-center mt-16 text-8xl text-blue-800 uppercase underline font-lucky space-x-10">
      <div v-for="(x, index) in 'wisielec'" :key="index">
        {{ x }}
      </div>
    </div>
    <div class="ml-60 my-40">
      <transition name="text" appear enter-active-class="transition-all duration-1000 ease-in"
        enter-from-class="opacity-0 -translate-x-[500px]">
        <img src="@/img/hangman.png" />
      </transition>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'HomePage',
  setup() {
    const name = 'wisielec'
    return {
      name
    }
  }
}
</script>
