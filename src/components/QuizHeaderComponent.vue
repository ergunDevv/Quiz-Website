<script setup>
import {defineProps} from 'vue'

const props = defineProps(['questionStatus','barPercentage'])

</script>

<template>
    <div>
        <header>
            <h2>Question {{props.questionStatus}}</h2>
            <div class="bar">
              <div class="completion" :style="{width:props.barPercentage}"></div>
            </div>
          </header>
    </div>
</template>


<style scoped> 

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

</style>