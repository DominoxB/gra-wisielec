<template>
  <div class="font-lucky">
    <div class="flex justify-center mt-16 text-8xl text-blue-800 uppercase underline space-x-10">
      <div v-for="(x, index) in 'wisielec'" :key="index">
        {{ x }}
      </div>
    </div>
    <div class="grid grid-cols-2 justify-center items-center mt-20">
      <transition name="text" appear enter-active-class="transition-all duration-1000 ease-in"
        enter-from-class="opacity-0 -translate-x-[500px]">
        <img src="@/img/hangman.png" class="mx-auto" />
      </transition>
      <transition name="text" appear enter-active-class="transition-all duration-1000 ease-in"
        enter-from-class="opacity-0 translate-x-[500px]">
        <div class="text-6xl mx-auto text-center">
          <span>start</span>
          <img src="@/img/arrow.png" class="mt-8 cursor-pointer" />
        </div>
      </transition>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'HomePage',
}
</script>
