<template>
  <div class="md:grid md:grid-cols-2 p-16">
    <!-- div z plansza wisielca -->
    <div class="mx-auto mb-8 md:mb-0">
      <img :src="imgSrc" v-if="wrongLetters.length > 0" />
    </div>
    <!-- div z hasłem i literami do wyboru -->
    <div>
      <!-- hasło -->
      <div class="md:mb-64 mt-4 justify-center flex uppercase font-lucky text-5xl underline space-x-10 flex-wrap">
        <div v-for="(x, index) in randomElement" :key="index">
          {{ checkLetters(x) ? x : '__' }}
        </div>
      </div>
      <!-- litery -->
      <div class="flex gap-1 md:gap-3 justify-center flex-wrap">
        <div class="rounded-md text-2xl md:text-4xl p-1 md:p-2 font-lucky" v-for="char in letters" :key="char"
          @click="selectLetters(char)"
          :class="checkLetters(char) ? 'text-slate-500 border-2 border-slate-500' : 'border-blue-400 cursor-pointer border-2 md:border-4'">
          <span>{{ char }}</span>
        </div>
      </div>
    </div>
  </div>
  <ModalLost v-if="wrongLetters.length >= 10" />
  <ModalWin v-if="chosenLetters === randomElement" />
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue'
import ModalLost from './ModalLost.vue'
import ModalWin from './ModalWin.vue'

export default defineComponent({
  name: 'GameContent',
  components: {
    ModalLost,
    ModalWin
  },
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
    const passwordsToGuess = [
      'matematyka',
      'czekoladki',
      'odkurzacz',
      'parostatek',
      'kangurzyca',
      'poduszkowiec',
      'pierniczki',
      'krakowiaczek',
      'zeszyty',
      'sobota',
      'marchewka',
      'mitochondrium',
      'batoniki',
      'kolczyki',
      'kasztany',
      'galaktyka'
    ]

    const randomElement = passwordsToGuess[Math.floor(Math.random() * passwordsToGuess.length)]
    const chosenLetters = ref([]) as any
    const wrongLetters = ref([]) as any

    const selectLetters = (char: string) => {
      chosenLetters.value.push(char)
      if (!randomElement.includes(char)) {
        wrongLetters.value.push(char)
      }
    }

    const checkLetters = (x: string) => {
      return chosenLetters.value.includes(x)
    }
    
    const imgSrc = computed(() => {
      return require(`../img/hang${wrongLetters.value.length}.png`)
      
    })

    return {
      letters,
      randomElement,
      chosenLetters,
      wrongLetters,
      imgSrc,
      selectLetters,
      checkLetters
    }
  }
})
</script>