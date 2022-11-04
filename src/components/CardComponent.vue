<script setup> 

    import { defineProps } from 'vue';
    import {RouterLink} from 'vue-router'
    
    const props = defineProps(['quiz'])

</script>

<template>
<RouterLink :to="`/quiz/${props.quiz.id}`">

  <div>
      <div class="card">
          <img :src="props.quiz.img" alt="">
          <div class="card-text">
            <h2>{{ props.quiz.name }}</h2>
            <p>{{props.quiz.questions.length}} questions</p>
          </div>
      </div>
  </div>
</RouterLink>
</template>


<style>


/* CARD */
.card{
    width:310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
    text-decoration: none;
  }
  
  .card img {
    width: 100%;
    height: 190px;
    margin:0;
  }
  
  .card .card-text {
    padding :0 5px;
    text-decoration: none;
  }
  
  .card .card-text {
    font-weight: bold;
  }
  </style>