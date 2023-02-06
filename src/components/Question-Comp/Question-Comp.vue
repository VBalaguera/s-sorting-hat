<template>
  <div class="flex flex-col p-2 md:p-2 min-h-1/3 border" id="questions">
    <div>
      <div class="flex flex-col items-center">
        <!-- <h1 class="text-sm md:text-lg">
          Question number {{ questionsIndex + 1 }}:
        </h1> -->
        <span
          :class="[
            { fadeOut: active },
            numberAnswers > 14 ? 'text-xs md:text-sm' : 'text-sm md:text-lg',
            'font-bold',
          ]"
          >{{ questionContent }}</span
        >
        <!-- <span class="text-sm md:text-lg"
          >Number of questions: {{ questionsNumber }}</span
        > -->
      </div>
      <div
        :class="[
          numberAnswers > 2 ? 'md:flex-col mt-1' : 'md:flex-row ',
          numberAnswers > 14 ? 'text-xs md:text-sm' : 'text-sm md:text-lg',
          'flex flex-col items-center justify-between mt-2',
        ]"
      >
        <button
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border   my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues1, questionAnswer1)"
          :disabled="loading"
        >
          {{ questionAnswer1 }}
        </button>
        <button
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border   my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues2, questionAnswer2)"
          :disabled="loading"
        >
          {{ questionAnswer2 }}
        </button>
        <button
          v-if="numberAnswers > 2"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border   my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues3, questionAnswer3)"
          :disabled="loading"
        >
          {{ questionAnswer3 }}
        </button>
        <button
          v-if="numberAnswers > 3"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border   my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues4, questionAnswer4)"
          :disabled="loading"
        >
          {{ questionAnswer4 }}
        </button>
        <button
          v-if="numberAnswers > 4"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border   my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues5, questionAnswer5)"
          :disabled="loading"
        >
          {{ questionAnswer5 }}
        </button>
        <button
          v-if="numberAnswers > 5"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border   my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues6, questionAnswer6)"
          :disabled="loading"
        >
          {{ questionAnswer6 }}
        </button>
        <button
          v-if="numberAnswers > 6"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border   my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues7, questionAnswer7)"
          :disabled="loading"
        >
          {{ questionAnswer7 }}
        </button>

        <!-- questions 8 to 15 -->

        <button
          v-if="numberAnswers > 14"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border  my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues8, questionAnswer8)"
          :disabled="loading"
        >
          {{ questionAnswer8 }}
        </button>
        <button
          v-if="numberAnswers > 14"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border  my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues9, questionAnswer9)"
          :disabled="loading"
        >
          {{ questionAnswer9 }}
        </button>
        <button
          v-if="numberAnswers > 14"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border  my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues10, questionAnswer10)"
          :disabled="loading"
        >
          {{ questionAnswer10 }}
        </button>
        <button
          v-if="numberAnswers > 14"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border  my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues11, questionAnswer11)"
          :disabled="loading"
        >
          {{ questionAnswer11 }}
        </button>
        <button
          v-if="numberAnswers > 14"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border  my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues12, questionAnswer12)"
          :disabled="loading"
        >
          {{ questionAnswer12 }}
        </button>
        <button
          v-if="numberAnswers > 14"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border  my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues13, questionAnswer13)"
          :disabled="loading"
        >
          {{ questionAnswer13 }}
        </button>
        <button
          v-if="numberAnswers > 14"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border  my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues14, questionAnswer14)"
          :disabled="loading"
        >
          {{ questionAnswer14 }}
        </button>
        <button
          v-if="numberAnswers > 14"
          :class="[
            { fadeOut: active },
            numberAnswers >= 4 ? 'p-1 md:p-1' : 'md:p-2',
            'btn border  my-1 mx-1 w-full',
          ]"
          @click="selectAnswer(questionValues15, questionAnswer15)"
          :disabled="loading"
        >
          {{ questionAnswer15 }}
        </button>

        <!--  -->
      </div>
    </div>
  </div>
</template>

<script>
import { nextTick } from 'vue'
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Question-Comp',
  props: {
    gameQuestions: Object,
  },
  data() {
    return {
      active: false,
      isGameOver: false,
      questionsIndex: 0,
      questionsNumber: 0,
      numberAnswers: 0,
      questionContent: '',
      questionAnswer1: '',
      questionValues1: '',
      questionAnswer2: '',
      questionValues2: '',
      questionAnswer3: '',
      questionValues3: '',
      questionAnswer4: '',
      questionValues4: '',
      questionAnswer5: '',
      questionValues5: '',
      questionAnswer6: '',
      questionValues6: '',
      questionAnswer7: '',
      questionValues7: '',
      questionAnswer8: '',
      questionValues8: '',
      questionAnswer9: '',
      questionValues9: '',
      questionAnswer10: '',
      questionValues10: '',
      questionAnswer11: '',
      questionValues11: '',
      questionAnswer12: '',
      questionValues12: '',
      questionAnswer13: '',
      questionValues13: '',
      questionAnswer14: '',
      questionValues14: '',
      questionAnswer15: '',
      questionValues15: '',
      questionAnswered: false,
      loading: false,
    }
  },
  mounted() {
    this.askQuestion()
  },
  methods: {
    // game ask a question
    async askQuestion() {
      // const numberOfQuestions =
      //   this.gameQuestions[this.questionsIndex].answers.length
      // console.log(
      //   'how many possible answers for this question?',
      //   numberOfQuestions
      // )
      const questions = this.gameQuestions
      const index = this.questionsIndex

      this.questionsNumber = questions.length

      this.questionContent = questions[index].title
      this.numberAnswers = questions[index].answers.length

      this.questionAnswer1 = questions[index].answers[0].title
      this.questionValues1 = questions[index].answers[0].scores
      this.questionAnswer2 = questions[index].answers[1].title
      this.questionValues2 = questions[index].answers[1].scores

      this.questionAnswer3 = questions[index].answers[2].title
      this.questionValues3 = questions[index].answers[2].scores
      this.questionAnswer4 = questions[index].answers[3].title
      this.questionValues4 = questions[index].answers[3].scores
      this.questionAnswer5 = questions[index].answers[4].title
      this.questionValues5 = questions[index].answers[4].scores

      this.questionAnswer6 = questions[index].answers[5].title
      this.questionValues6 = questions[index].answers[5].scores
      this.questionAnswer7 = questions[index].answers[6].title
      this.questionValues7 = questions[index].answers[6].scores
      this.questionAnswer8 = questions[index].answers[7].title
      this.questionValues8 = questions[index].answers[7].scores
      this.questionAnswer9 = questions[index].answers[8].title
      this.questionValues9 = questions[index].answers[8].scores
      this.questionAnswer10 = questions[index].answers[9].title
      this.questionValues10 = questions[index].answers[9].scores
      this.questionAnswer11 = questions[index].answers[10].title
      this.questionValues11 = questions[index].answers[10].scores
      this.questionAnswer12 = questions[index].answers[11].title
      this.questionValues12 = questions[index].answers[11].scores
      this.questionAnswer13 = questions[index].answers[12].title
      this.questionValues13 = questions[index].answers[12].scores
      this.questionAnswer14 = questions[index].answers[13].title
      this.questionValues14 = questions[index].answers[13].scores
      this.questionAnswer15 = questions[index].answers[14].title
      this.questionValues15 = questions[index].answers[14].scores
    },
    async prepareNextQuestion() {
      if (!this.isGameOver) {
        this.questionsIndex++
        this.askQuestion()
        await nextTick()
        window.scrollTo(0, document.body.scrollHeight)
      }
    },
    checkIfLastRound() {
      if (this.questionsIndex == this.questionsNumber - 1) {
        this.isGameOver = true
        this.$emit('game-over')
      }
    },
    // user selects answer
    selectAnswer(answers, answer) {
      this.active = true
      this.loading = true

      setTimeout(() => {
        this.loading = false
        this.active = false

        this.prepareNextQuestion()

        this.checkIfLastRound()
      }, 2000)

      const answeredQuestion = {
        content: this.questionContent,
        answerSelected: answer,
      }
      this.$emit('add-answered-question', answeredQuestion)
      // console.log('answers values', answers)

      this.$emit('select-answer', answers)
    },
  },
}
</script>

<style scoped>
.fadeOut {
  animation: fadeOut 2s;
}
</style>
