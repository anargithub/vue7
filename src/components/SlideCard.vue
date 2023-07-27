<template>
    <div class="card">
      <div @click="emits(`prev`, props.slideId)" class="button" id="prev">previous</div>
      <div>
        <h3>{{ props.title }}</h3>
        <h5>{{ props.body }}</h5>
      </div>
      <div @click="emits('next', props.slideId)" class="button" id="next">next</div>
    </div>
  </template>
  
  <script setup lang="ts">
  interface Props {
    title: string
    body: string
    slideId: number
  }
  const props = defineProps<Props>()
  
  interface Emits{
    (e:'next', id:number):void
    (e:'prev', id:number):void
  }
  const emits = defineEmits<Emits>()
  </script>
  
  <style scoped>
  .card {
    color: black;
    border-radius: 15px;
    width: 400px;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: space-between;

  }
  .button {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 15px;
    width: 100px;
    height: 40px;
    border: 1px solid black;
  }

  </style>