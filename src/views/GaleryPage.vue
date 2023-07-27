<template>
    <div>
      <router-link :to="{ name: 'HomePage' }">Home page</router-link>
      <slide-card
        v-for="slide in content"
        @prev="(slideId:any)=>prevSlide(slideId)"
        @next="(slideId:any)=>nextSlide(slideId)"
        v-show="slide.view"
        :key="slide.id"
        :slideId="slide.id"
        :title="slide.title"
        :body="slide.body"
      ></slide-card>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue'

import SlideCard from '@/components/SlideCard.vue'
  const content = ref([
    {
      id: 1,
      view: true,
      title: 'title 1',
      body: 'body 1'
    },
    {
      id: 2,
      view: false,
      title: 'title 2',
      body: 'body 2'
    },
    {
      id: 3,
      view: false,
      title: 'title 3',
      body: 'body 3',
    }
  ])
  function prevSlide(id:number) {
    if (id != 1) {
      content.value[id-2].view = true
      content.value[id-1].view = false
    }else{
      content.value[content.value.length-1].view = true
      content.value[id-1].view = false
    }
  }
  function nextSlide(id:number){
    if(id != content.value.length){
      content.value[id].view = true
      content.value[id-1].view = false
    }else{
      content.value[0].view = true
      content.value[id-1].view = false
    }
  }
  </script>
  
  <style scoped></style>
  