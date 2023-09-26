<template>
  <div class="p-16 md:grid md:grid-cols-2">
    <!-- div z plansza wisielca -->
    <div class="hidden md:flex mx-auto mb-8 md:mb-0">
      <img :src="imgSrc" v-if="wrongLetters.length > 0" />
    </div>
    <!-- div z hasłem i literami do wyboru -->
    <div>
      <!-- hasło -->
      <div
        class="md:mb-64 mt-4 justify-center flex uppercase font-lucky text-4xl md:text-5xl underline gap-4 md:gap-x-10 flex-wrap whitespace-nowrap gap-y-2">
        <div v-for="(x, index) in randomPassword" :key="index">
          {{ checkLetters(x) ? x : '__' }}
        </div>
      </div>
      <!-- litery -->
      <div class="flex mt-10 md:mt-0 gap-1 md:gap-3 justify-center flex-wrap">
        <button
          class="cursor-pointer border-2 md:border-4 border-blue-400 disabled:border-slate-500 disabled:text-slate-500 rounded-md text-2xl md:text-4xl p-1 md:p-2 font-lucky"
          v-for="char in letters" :key="char" @click="selectLetters(char)" :disabled="chosenLetters.includes(char)">
          <span>{{ char }}</span>
        </button>
      </div>
    </div>
    <div class="mx-auto mt-16 md:mb-0 md:hidden">
      <img :src="imgSrc" v-if="wrongLetters.length > 0" />
    </div>
  </div>
  <ModalLost v-if="wrongLetters.length >= 10" @new-game="agree" @cancel-action="cancel" />
  <ModalWin v-if="containsAll" @new-game="agree" @cancel-action="cancel" />
</template>

<script lang="ts">
import { defineComponent, ref, computed, onMounted } from 'vue'
import ModalLost from './ModalLost.vue'
import ModalWin from './ModalWin.vue'

export default defineComponent({
  name: 'GameContent',
  components: {
    ModalLost,
    ModalWin
  },
  emits: ['cancel'],
  setup(props, context) {
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
      'galaktyka',
      'rowerzysta',
      'miniaturka',
      'porzeczka',
      'warsztaty'
    ]

    const chosenLetters = ref([]) as any
    const wrongLetters = ref([]) as any

    const randomPassword = ref('')

    const getPassword = () => {
      randomPassword.value = passwordsToGuess[Math.floor(Math.random() * passwordsToGuess.length)]
    }

    onMounted(() => {
      getPassword()
    })

    const selectLetters = (char: string) => {
      chosenLetters.value.push(char)
      if (!randomPassword.value.includes(char)) {
        wrongLetters.value.push(char)
      }
    }

    const checkLetters = (x: string) => {
      return chosenLetters.value.includes(x)
    }

    const imgSrc = computed(() => {
      return require(`../img/hang${wrongLetters.value.length}.png`)

    })

    const splitRandomPassword = computed(() => randomPassword.value.split(''))

    const containsAll = computed(() => splitRandomPassword.value.every(element => {
      return chosenLetters.value.includes(element)
    }) && splitRandomPassword.value.length > 0)

    const clean = () => {
      wrongLetters.value = []
      chosenLetters.value = []
      getPassword()
    }

    const agree = () => {
      clean()
    }

    const cancel = () => {
      context.emit('cancel')
      clean()
    }

    return {
      letters,
      randomPassword,
      chosenLetters,
      wrongLetters,
      imgSrc,
      containsAll,
      selectLetters,
      checkLetters,
      agree,
      cancel
    }
  }
})
</script>
