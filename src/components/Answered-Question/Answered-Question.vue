<template>
  <div class="flex flex-col p-2 md:p-4 h-full overflow-auto">
    <div
      class="flex w-100 h-100 flex flex-col"
      v-for="answeredQuestion in answeredQuestions"
      :key="answeredQuestion.id"
    >
      <div>
        <div class="flex justify-start w-full items-center my-2 fadeInQuestion">
          <img
            src="../../assets/sorting-hat-transparent-bg.png"
            alt="sorting hat"
            class="h-[18px] w-[18px] md:h-[28px] md:w-[28px] mr-2 md:mr-4"
          />
          <span class="text-sm md:text-lg text-start">{{
            answeredQuestion.content
          }}</span>
        </div>
        <div class="flex justify-end w-full items-center my-2 fadeInAnswer">
          <span class="text-sm md:text-lg font-bold mr-2 md:mr-4">Me: </span>
          <span class="text-sm md:text-lg text-end">{{
            answeredQuestion.answerSelected
          }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AnsweredQuestion',
  props: {
    answeredQuestions: Array,
  },
}
</script>

<style scoped>
.fadeInQuestion {
  animation: fadeIn 1s;
}

.fadeInAnswer {
  animation: fadeIn 2s;
}
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  66% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
