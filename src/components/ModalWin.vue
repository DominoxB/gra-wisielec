<template>
  <div
    class="bg-slate-400 fixed top-0 left-0 h-screen w-screen z-50 opacity-80"
  ></div>
  <div class="relative z-50 font-lucky">
    <div
      class="bg-white fixed left-1/2 top-1/2 transform -translate-x-1/2 -translate-y-1/2 border-2 border-indigo-900 rounded-2xl p-10 text-center"
    >
      <span class="text-2xl">Gratulujemy!!! :)</span>
      <p class="text-2xl">Gramy jeszcze raz?</p>
      <div class="flex justify-center mt-10">
        <button
          @click="clickYes"
          class="border border-black hover:bg-green-200 rounded text-center text-lg p-2 mr-10"
        >
          Tak
        </button>
        <button
          @click="clickCancel"
          class="w-[136px] border border-black hover:bg-red-200 rounded text-center text-lg p-1"
        >
          Anuluj
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalLost",
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
}
</script>
