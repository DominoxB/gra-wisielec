<template>
  <div class="grid grid-cols-2 p-16">
    <!-- div z plansza wisielca -->
    <div class="w-96 h-[500px] border border-black mx-auto">tu bedzie rysowany wisielec</div>
    <!-- div z hasłem i literami do wyboru -->
    <div>
      <!-- hasło -->
      <div class="mb-80 justify-center flex">Tu będzie hasło</div>
      <!-- litery -->
      <div class="flex gap-3 justify-center flex-wrap">
        <div class="border-4 rounded-md border-blue-300 text-4xl p-2 font-lucky cursor-pointer" v-for="char in letters"
          :key="char">
          <span>{{ char }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'GameContent',
  setup() {
    const letters = [
      'a',
      'b',
      'c',
      'd',
      'e',
      'f',
      'g',
      'h',
      'i',
      'j',
      'k',
      'l',
      'm',
      'n',
      'o',
      'p',
      'q',
      'r',
      's',
      't',
      'u',
      'v',
      'w',
      'x',
      'y',
      'z',
    ]
    return {
      letters
    }
  }
})
</script>