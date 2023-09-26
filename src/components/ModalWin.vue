<template>
  <div class="bg-slate-400 fixed top-0 left-0 h-screen w-screen z-50 opacity-80"></div>
  <transition name="text" appear enter-active-class="transition-all duration-1000 ease-in-out"
    enter-from-class="opacity-0">
    <div class="relative z-50 font-lucky transition ease-in-out delay-200">
      <div
        class="bg-blue-100 fixed left-1/2 top-1/2 transform -translate-x-1/2 -translate-y-1/2 border-2 border-indigo-900 rounded-2xl p-10 md:p-24 text-center">
        <span class="text-2xl">Gratulujemy!!! :)</span>
        <p class="text-2xl">Gramy jeszcze raz?</p>
        <div class="flex justify-center mt-10">
          <button @click="clickYes"
            class="border border-black hover:bg-blue-200 rounded text-center text-lg p-2 mr-10 hover:-translate-y-1 hover:scale-110 duration-300">
            Tak
          </button>
          <button @click="clickCancel"
            class="w-[136px] border border-black hover:bg-blue-200 rounded text-center text-lg p-1 hover:-translate-y-1 hover:scale-110 duration-300">
            Anuluj
          </button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: "ModalWin",
  emits: ['new-game', 'cancel-action'],
  setup(props, context) {
    const clickYes = () => {
      context.emit('new-game')
    }
    const clickCancel = () => {
      context.emit("cancel-action")
    }

    return {
      clickYes,
      clickCancel,
    }
  }
})
</script>
