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
    id: 3001,
    text: 'ОПРЕДЕЛЕНИЕ МАСШТАБА ТОПОГРАФИЧЕСКОЙ КАРТЫ',
    redText: '',
    after: '',
    img: '3001.jpg'
  },
  {
    id: 3002,
    text: 'Нужно измерить расстояние на карте между линиями координатной сетки и определить, через какое количество километров проведены эти линии',
    redText: 'ПО КООРДИНАТНОЙ СЕТКЕ',
    after: '',
    img: '3002.jpg'
  },
  {
    id: 3003,
    text: 'Нужно измерить расстояние на карте между линиями координатной сетки и определить, через какое количество километров проведены эти линии',
    redText: 'ПО КООРДИНАТНОЙ СЕТКЕ',
    after: '',
    img: '3003.jpg'
  },
  {
    id: 3004,
    text: 'Нужно измерить расстояние на карте между линиями координатной сетки и определить, через какое количество километров проведены эти линии',
    redText: 'ПО КООРДИНАТНОЙ СЕТКЕ',
    after: '',
    img: '3004.jpg'
  },
  {
    id: 3005,
    text: 'Нужно измерить расстояние на карте между линиями координатной сетки и определить, через какое количество километров проведены эти линии',
    redText: 'ПО КООРДИНАТНОЙ СЕТКЕ',
    after: '',
    img: '3005.jpg'
  },
  {
    id: 3006,
    text: 'Нужно измерить расстояние на карте между линиями координатной сетки и определить, через какое количество километров проведены эти линии',
    redText: 'ПО КООРДИНАТНОЙ СЕТКЕ',
    after: '',
    img: '3006.jpg'
  },
  {
    id: 3007,
    text: 'Например, если на карте имеется дорога с километровыми столбами, то масштаб удобнее всего определять по расстоянию между ними.',
    redText: 'ПО РАССТОЯНИЯМ МЕЖДУ МЕСТНЫМИ ОБЪЕКТАМ.',
    after: 'УСЛОВНЫЙ ЗНАК «КИЛОМЕТРОВЫЙ СТОЛБ»',
    img: '3007.jpg'
  }
])
</script>

<template>
  <div class="fill">
    <swiper
      :modules="modules"
      :slides-per-view="1.1"
      :loop="false"
      :space-between="100"
      :centered-slides="true"
      :pagination="true"
      @swiper="onSwiper"
      navigation
    >
      <swiper-slide v-for="question in questions" :key="question.id">
        <div class="slide-content">
          <div class="question-red-text" v-if="question.redText !== ''">{{ question.redText }}</div>
          <div class="question-text">{{ question.text }}</div>
          <div class="question-text" v-if="question.after !== ''">{{ question.after }}</div>
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
  align-items: flex-start;
  justify-content: center;
  font-size: 100%;
}

.question-text,
.question-red-text {
  font-weight: bolder;
  width: 100%;
  margin-bottom: 8px;
  font-size: 150%;
}

.question-red-text {
  color: red;
}

.question-image img {
  max-width: 90%;
  height: 400px;
}

@media screen and (min-width: 1800px) {
  .swiper {
    width: 1600px;
    height: 100%;
    padding: 1% 0;
  }

  .question-image img {
    height: 600px;
  }
}
</style>
