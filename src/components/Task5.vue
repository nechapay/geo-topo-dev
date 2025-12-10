<script setup>
import { computed, ref, reactive, watch, onMounted } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination, Navigation } from 'swiper/modules'

import _ from 'lodash'

import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'

const swiperInstance = ref(null)

const onSwiper = (swiper) => {
  swiperInstance.value = swiper
}

const modules = [Pagination, Navigation]

onMounted(() => {
  questions.value.forEach((question) => {
    question.opt = _.shuffle(question.opt)
  })
})

const questions = ref([
  {
    id: 5001,
    text: 'Картографические условные знаки это символические графические обозначения, которые используются для изображения на картах различных объектов и их характеристик',
    redText: '',
    img: ''
  },
  {
    id: 5002,
    text: '',
    redText: '',
    img: '5001.jpg',
    disabled: false
  },
  {
    id: 5003,
    text: '',
    redText: '',
    img: '5002.jpg',
    disabled: false
  },
  {
    id: 5004,
    text: '',
    redText: '',
    img: '5003.jpg',
    disabled: false
  }
])
</script>

<template>
  <div class="fill">
    <swiper
      :modules="modules"
      :slides-per-view="1.1"
      :loop="false"
      :space-between="80"
      :centered-slides="true"
      :pagination="true"
      @swiper="onSwiper"
      navigation
    >
      <swiper-slide v-for="question in questions" :key="question.id">
        <div class="slide-content">
          <div class="question-text">{{ question.text }}</div>
          <div class="question-red-text" v-if="question.redText !== ''">{{ question.redText }}</div>
          <div class="question-image"><img :src="`img\\${question.img}`" alt="" /></div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<style scoped>
.swiper {
  width: 1100px;
  height: 100%;
  padding: 1% 0;
}

.swiper-slide {
  height: 95%;
  border-radius: 8px;
  box-shadow: 2px 4px 8px grey;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 100%;
}

.question-text,
.question-red-text {
  font-weight: bolder;
  width: 100%;
  margin-bottom: 8px;
  font-size: 250%;
}

.question-red-text {
  color: red;
}

.question-image img {
  max-width: 90%;
  height: 600px;
}

@media screen and (min-width: 1800px) {
  .swiper {
    width: 1600px;
    height: 100%;
    padding: 1% 0;
  }

  .question-image img {
    height: 500px;
  }
}
</style>
