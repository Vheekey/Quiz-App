<template>
    <div class="question-box-container mt-3">
        <b-jumbotron>
            <template v-slot:lead>
                {{ currentQuestion.question }}
            </template>

            <hr class="my-4">

            <p v-for="(answer, index) in answers" :key="index">
                {{ answer }}
            </p>

            <b-button variant="success" href="#" class="btn-md mr-1">Submit</b-button>
            <b-button @click="next" variant="dark" href="#" class="btn-md ml-1">Next</b-button>
        </b-jumbotron>
    </div>
</template>

<script>
export default {
  props: {
    //to display any variables that was passed from another component to this component, it must be referenced in props with the datatype
    currentQuestion: Object,
    next: Function
  },
  computed:{
      answers(){
          let answers = [...this.currentQuestion.incorrect_answers] //duplicating the main array instead of referencing
            answers.push(this.currentQuestion.correct_answer)
            return answers

      }
  },
  mounted(){
      console.log(this.currentQuestion)
  }
}
</script>