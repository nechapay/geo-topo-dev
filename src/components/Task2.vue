<script setup>
import { computed, ref, reactive, watch, onMounted } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination, Navigation } from 'swiper/modules'

import _, { forEach } from 'lodash'

import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'

const swiperInstance = ref(null)

const score = ref(0)

const onSwiper = (swiper) => {
  swiperInstance.value = swiper
}

const modules = [Pagination, Navigation]

onMounted(() => {})
const questions = ref([
  {
    id: 2001,
    text: 'Изучите фрагмент топографической карты и ответь на вопросы.',
    img: '2001.jpg',
    disabled: false,
    q: [
      {
        id: 2001001,
        label:
          'А. Определите максимальную и минимальную высоты участка местности, изображённого на фрагменте топографической карты.',
        value: '',
        placeholder: 'Ответ - 2 цифры через и с точностью до десятых',
        status: '',
        answer: ['186,9м и 102,0м', '186,9м 102,0м', '186,9 и 102,0', '186,9м и 102м', '186,9 и 102', '186,9м 102м'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2001002,
        label: 'Б. Какое происхождение имеют озёра, расположенные в бассейне реки Уй?',
        value: '',
        placeholder: 'Ответ',
        status: '',
        answer: ['озёра-старицы', 'пойменные озёра'],
        class: {
          correct: false,
          incorrect: false
        }
      }
    ]
  }
])

function handleSubmit() {
  disableQuestion()
  questions.value[getIndex()].q.forEach((item, index) => {
    item.status = item.answer.includes(item.value.toLowerCase()) ? 'Верно' : 'Неверно'
    item.class.correct = item.answer.includes(item.value.toLowerCase())
    item.class.incorrect = !item.answer.includes(item.value.toLowerCase())
  })
}

function disableQuestion() {
  questions.value[getIndex()].disabled = true
}

function getIndex() {
  let index = 0
  if (!_.isNil(swiperInstance)) {
    if (!_.isNil(swiperInstance.value)) {
      index = swiperInstance.value.activeIndex
    }
  }
  return index
}
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
        <div class="slide-content fill">
          <div class="my-grid fill">
            <div class="question-image"><img :src="`img\\${question.img}`" alt="" /></div>
            <div class="question-text">{{ question.text }}</div>
            <div class="question-controls">
              <div class="question-input" v-for="item in question.q" :key="item.id" :class="item.class">
                <label for="">{{ item.label }}</label>
                <input type="text" v-model="item.value" :disabled="question.disabled" :placeholder="item.placeholder" />
                <div class="input-status">{{ item.status }}</div>
              </div>
              <button class="my-button" @click="handleSubmit" v-if="!question.disabled">Ответить</button>
            </div>
          </div>
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

.my-grid {
  display: grid;
  grid-template-columns: 2fr 3fr;
  grid-template-rows: 2fr 4fr;
  justify-content: center;
}

.question-text {
  font-weight: bolder;
  width: 100%;
  margin-bottom: 8px;
  font-size: 150%;
  grid-column: 2;
  grid-row: 1;
}

.question-image {
  grid-column: 1;
  grid-row: 1 / 3;
  display: flex;
  align-items: flex-start;
  justify-content: center;
}

.question-image img {
  margin-top: 12px;
  max-width: 90%;
  height: 500px;
}

.question-input {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  padding: 10px;
  font-size: 120%;
}

input {
  width: 100%;
  height: 45px;
  padding: 12px;
  border-radius: 4px;
  border: 1.5px solid lightgrey;
  outline: none;
  transition: all 0.3s cubic-bezier(0.19, 1, 0.22, 1);
  box-shadow: 0px 0px 20px -18px;
}

input:hover {
  border: 2px solid lightgrey;
  box-shadow: 0px 0px 20px -17px;
}

input:active {
  transform: scale(0.95);
}

input:focus {
  border: 2px solid grey;
}

.input-status {
  text-transform: uppercase;
}

.question-input.correct input {
  color: green;
  border: 1.5px solid green;
}

.question-input.incorrect input {
  color: red;
  border: 1.5px solid red;
}

.question-input.correct .input-status {
  color: green;
}

.question-input.incorrect .input-status {
  color: red;
}

@media screen and (min-width: 1800px) {
  .swiper {
    width: 1600px;
    height: 100%;
    padding: 1% 0;
  }
}
</style>
