<template>
    <div >
      <header>
        <h1>Quizes</h1>
        <input v-model.trim="search" type="text" placeholder="Search..." />
      </header>
      <div class="options-container">
        <CardComponent v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from "vue";
  import qData from "../data/quizes.json";
  import CardComponent from "../components/CardComponent.vue";
  
  const quizes = ref(qData);
  const search = ref("");


  
  watch(search, () => {
    quizes.value = qData.filter((quiz) =>
      quiz.name.toLowerCase().includes(search.value.toLowerCase())
    );
  });
  </script>
  
  
  <style scoped>

  header {
    margin-bottom: 10px;
    margin-top: 10px;
    display: flex;
    align-items: center;
  }
  header h1 {
    font-weight: bold;
    margin-right: 25px;
  }
  header input {
    border: none;
    background-color: rgba(128, 128, 128, 0.1);
    padding: 20px;
    border-radius: 5px;
  }
  .options-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
  }
  </style>