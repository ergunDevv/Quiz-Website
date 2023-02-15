<script setup>

import QuestionComponent from "../components/QuestionComponent.vue"
import QuizHeader from "../components/QuizHeaderComponent.vue"
import { useRoute } from "vue-router";
import { ref } from "vue";
import quizes from '../data/quizes.json'

const route =useRoute();

const quizId=parseInt(route.params.id)

const quiz = quizes.find(q=>q.id === quizId);

const currentQuestionIndex = ref(0);


</script>

<template>
  <div>
        <QuizHeader/>
    <div>
        <QuestionComponent :question="quiz.questions[currentQuestionIndex]"/>

    </div>
  </div>
</template>

<style scoped>
header {
  margin-top: 20px;
}
header h4 {
  font-size: 30px;
}
.bar {
  width: 300px;
  height: 50px;
  border: 3px solid bisque;
}

.completion {
  height: 100%;
  width: 0%;
  background-color: bisque;
}

/* */
.question-container{
    margin-top:20px;
}

.question{
    font-size: 40px;
    margin-bottom: 20px;
}

.option{
    display: flex;
    margin-bottom: 20px;
    cursor: pointer;
}

.option-label{
    background-color: bisque;
    width: 50px;
    height: 50px;
    font-size:30px;
    display: flex;
    align-items: center;
    justify-content: center;

}

.option-value{
    background-color: rgb(244, 239, 239);
    width: 100%;
    font-size: 30px;
    height: 50px;
    padding: 0 20px;
    display: flex;
    align-self: center;
    align-items: center;
}

</style>