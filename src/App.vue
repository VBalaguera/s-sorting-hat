<template>
  <div class="bg-neutral-600 min-h-screen p-2 md:p-4">
    <div class="flex flex-col justify-center w-full items-center">
      <div class="w-full md:w-3/5">
        <!-- username form -->
        <div
          v-if="showUsernameForm"
          class="fadeIn flex flex-col justify-center items-center h-full h-[48rem]"
        >
          <div>
            <h1 class="text-md md:text-lg font-bold">
              Welcome to the sorting hat app
            </h1>
            <span class="text-sm md:text-lg"
              >Where your magic house will be selected</span
            >
            <img
              class="w-[400px]"
              src="https://i.ibb.co/NFsD0t0/Hogwarts-crest.png"
              alt="Welcome to the sorting hat app!"
            />
          </div>
          <div class="mt-4">
            <h1 class="mb-2 text-sm md:text-lg">Please enter your name:</h1>
            <form
              @submit="handleSubmitName"
              class="flex flex-col items-center w-full"
            >
              <input
                class="p-2 mb-2 w-[200px] md:w-[350px] text-sm md:text-lg text-black"
                type="text"
                name="username"
                v-model="username"
                required
              />
              <button
                class="btn w-[200px] md:w-[350px] border text-sm md:text-lg"
                type="submit"
              >
                enter
              </button>
            </form>
          </div>
        </div>
        <!--  -->
        <!-- message while playing the game -->
        <div
          class="flex flex-col p-2"
          v-if="username !== '' && !isGameOver && !showUsernameForm"
        >
          <h1 class="mb-2 text-sm md:text-lg">
            {{ username }}, choose wisely...
          </h1>
          <span class="mb-2 text-sm md:text-lg"
            >The sorting hat is listening...</span
          >
        </div>
        <!--  -->

        <!-- game -->
        <div
          class="flex flex-col justify-between min-h-[48rem] overflow-auto"
          v-if="username !== '' && !isGameOver && !showUsernameForm"
        >
          <!-- answered questions -->

          <AnsweredQuestion :answeredQuestions="answeredQuestions" />
          <!--  -->

          <!-- question and options -->
          <QuestionComp
            :gameQuestions="gameQuestions"
            @select-answer="selectAnswer"
            @add-answered-question="addAnsweredQuestion"
            @game-over="gameOver"
          />
        </div>
        <!--  -->
        <!-- final results when game is finished -->
        <Result
          v-if="isGameOver"
          :winner="winner"
          :username="username"
          @reset-game="resetGame"
        />
        <!--  -->
      </div>
    </div>
  </div>
</template>

<script>
import QuestionComp from '@/components/Question-Comp/Question-Comp'
import AnsweredQuestion from './components/Answered-Question/Answered-Question.vue'
import Result from './components/Result/Result.vue'

import gameQuestions from './data/sorting_hat.json'

import { nextTick } from 'vue'

export default {
  name: 'App',
  data() {
    return {
      showUsernameForm: true,
      username: '',
      gameQuestions: gameQuestions,
      isGameOver: false,
      result: {
        g: 0,
        h: 0,
        s: 0,
        r: 0,
      },
      winner: '',
      answeredQuestions: [],
    }
  },
  components: {
    // eslint-disable-next-line vue/no-unused-components
    QuestionComp,
    Result,
    AnsweredQuestion,
  },
  methods: {
    // get user's name
    handleSubmitName(e) {
      e.preventDefault()
      const username = this.username
      this.username = username
      this.showUsernameForm = false
    },
    // answer selected by user updates state
    async selectAnswer(answers) {
      this.result.g = this.result.g + answers.g
      this.result.s = this.result.s + answers.s
      this.result.h = this.result.h + answers.h
      this.result.r = this.result.r + answers.r

      // console.log('updated score Gryffindor', this.result.g)
      // console.log('updated score Slytherin', this.result.s)
      // console.log('updated score Hufflepuff', this.result.h)
      // console.log('updated score Ravenclaw', this.result.r)

      // automatically scrolls to the bottom of page
      await nextTick()
      window.scrollTo(0, document.body.scrollHeight)
    },
    // and answered question to answeredQuestions array for displaying
    addAnsweredQuestion(question) {
      // console.log(
      //   'question: ',
      //   question.content,
      //   'answer: ',
      //   question.answerSelected
      // )
      const answeredQuestions = [...this.answeredQuestions, question]
      this.answeredQuestions = answeredQuestions
    },
    // calculate final result
    calculateResult() {
      this.winner = Object.keys(this.result).reduce((a, b) =>
        this.result[a] > this.result[b] ? a : b
      )
      // console.log('winner', this.winner)
    },
    // is the game over?
    gameOver() {
      this.isGameOver = true
      this.calculateResult()
    },
    // user wants to play again?
    resetGame() {
      this.showUsernameForm = true
      this.username = ''
      this.gameQuestions = gameQuestions
      this.isGameOver = false
      this.result.g = 0
      this.result.h = 0
      this.result.s = 0
      this.result.r = 0
      this.winner = null
      this.answeredQuestions = []
    },
  },
}
</script>

<style>
#app {
  font-family: 'Lora', serif, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
}

.btn {
  transition: all 0.5s ease-in-out;
}

.btn:hover {
  color: gold;

  filter: brightness(80%);
}

.fadeIn {
  animation: fadeIn 3s;
}
</style>
