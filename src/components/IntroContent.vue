<template>
  <div class="md:grid md:grid-cols-2 justify-center items-center mt-12 md:mt-20 font-lucky">
    <transition name="text" appear enter-active-class="transition-all duration-1000 ease-in"
      enter-from-class="opacity-0 -translate-x-[500px]">
      <img src="@/img/hangman.png" class="mx-auto mb-10 md:mb-0" />
    </transition>
    <transition name="text" appear enter-active-class="transition-all duration-1000 ease-in"
      enter-from-class="opacity-0 translate-x-[500px]">
      <div class="text-6xl mx-auto text-center">
        <span>start</span>
        <img src="@/img/arrow.png" class="mt-8 cursor-pointer mx-auto" @click="$emit('clickPlay')" />
      </div>
    </transition>
  </div>
</template>

<script lang="ts" >
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IntroContent',
  emits: ['clickPlay']
})
</script>
