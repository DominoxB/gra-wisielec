<template>
  <div class="font-lucky">
    <div class="flex justify-center mt-16 text-6xl md:text-8xl text-blue-800 uppercase underline space-x-4 md:space-x-10">
      <div v-for="(x, index) in 'wisielec'" :key="index">
        {{ x }}
      </div>
    </div>
  </div>
  <IntroContent v-if="isStartView" @click-play="play" />
  <GameContent v-else @cancel="isStartView = true" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import IntroContent from './IntroContent.vue'
import GameContent from './GameContent.vue'

export default defineComponent({
  name: 'HomePage',
  components: {
    IntroContent,
    GameContent
  },
  setup() {
    const isStartView = ref(true)
    const play = () => {
      isStartView.value = !isStartView.value
    }
    return {
      isStartView,
      play
    }
  }
})
</script>
