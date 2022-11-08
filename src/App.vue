<template>
  <div class="container">
    <header>
      <h1>Quizes</h1>
      <input v-model.trim="search" type="text" placeholder="Search...">

    </header>
    <div class="options-container">
      <div v-for="quiz in quizes" :key="quiz.id" class="card">
          <img :src="quiz.img" alt="">
          <div class="card-text">
            <h2>{{ quiz.name }}</h2>
            <p>{{quiz.questions.length}} questions</p>
          </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref , watch } from 'vue';
import qData from './data/quizes.json'

const quizes = ref(qData);
const search = ref("");

watch(search,  ()=>{
  quizes.value = qData.filter(quiz=>quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})

</script>


<style scoped>

.container{
  max-width: 1000px;
  margin: 0 auto;
}
header{
  margin-bottom: 10px;
  margin-top:10px;
  display: flex;
  align-items: center;
}
header h1 {
  font-weight: bold;
  margin-right: 25px;
}
header input{
  border:none;
  background-color: rgba(128,128,128,0.1);
  padding: 20px;
  border-radius: 5px;

}
.options-container{
  display: flex;
  flex-wrap: wrap;
  margin-top:40px
}

/* CARD */
.card{
  width:310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
}

.card img {
  width: 100%;
  height: 190px;
  margin:0;
}

.card .card-text {
  padding :0 5px
}

.card .card-text {
  font-weight: bold;
}


</style>