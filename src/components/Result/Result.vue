<template>
  <div class="h-full h-[48rem] flex items-center justify-center p-2 md:p-4">
    <div class="flex flex-col items-center justify-center">
      <div class="flex flex-col">
        <span class="text-md md:text-lg fadeInName"
          >{{ username }}, the sorting hat has decided...</span
        >
        <span class="text-3xl font-bold fadeInText"
          >{{ houseWinner.name }}!</span
        >
      </div>
      <img
        class="w-[400px] fadeInWinnerHouse my-4"
        :src="houseWinner.imgUrl"
        :alt="houseWinner.name"
      />
      <button
        @click="resetGame"
        class="fadeInButton btn border p-1 md:p-4 text-sm md:text-lg my-2"
      >
        Would you like to play again?
      </button>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Result',
  data() {
    return {
      houseWinner: {
        name: '',
        imgUrl: '',
        text: '',
      },
    }
  },
  props: {
    winner: String,
    username: String,
  },
  mounted() {
    this.evaluateWinner()
  },
  methods: {
    evaluateWinner() {
      switch (this.winner) {
        case 'g':
          this.houseWinner.name = 'Gryffindor'
          this.houseWinner.imgUrl =
            'https://i.ibb.co/rZGmXmy/Gryffindor-crest.png'
          break
        case 'r':
          this.houseWinner.name = 'Ravenclaw'
          this.houseWinner.imgUrl =
            'https://i.ibb.co/2WVkg6Q/Ravenclaw-crest.png'
          break
        case 's':
          this.houseWinner.name = 'Slytherin'
          this.houseWinner.imgUrl =
            'https://i.ibb.co/JckxsZd/Slytherin-crest.png'
          break
        case 'h':
          this.houseWinner.name = 'Hufflepuff'
          this.houseWinner.imgUrl =
            'https://i.ibb.co/YRLTQF3/Hufflepuff-crest.png'
          break
        default:
          this.houseWinner.name = 'None, what happened?'
          this.houseWinner.imgUrl =
            'https://i.ibb.co/NYSDBSf/sorting-hat-transparent-bg.png'
          console.log('We do not have a winner, somehow. Ooops.')
      }
    },
    resetGame() {
      this.$emit('reset-game')
    },
  },
}
</script>

<style scoped>
.fadeInName {
  animation: fadeIn 3s;
}

.fadeInText {
  animation: fadeIn 6s;
}

.fadeInWinnerHouse {
  animation: fadeIn 10s;
}
.fadeInButton {
  animation: fadeIn 13s;
}
</style>
