<script setup>
import { computed, ref, reactive, watch, onMounted } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination, Navigation } from 'swiper/modules'

import MapCanvas from './MapCanvas.vue'

import _ from 'lodash'

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
    width: 500,
    height: 600,
    minZoom: 0.7,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.75,
    disabled: false,
    q: [
      {
        id: 2001001,
        label:
          'А. Определите максимальную и минимальную высоты участка местности, изображённого на фрагменте топографической карты.',
        value: '',
        placeholder: 'Ответ - 2 числа через и с точностью до десятых',
        status: '',
        score: 1,
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
        score: 1,
        answer: ['озёра-старицы', 'пойменные озёра'],
        class: {
          correct: false,
          incorrect: false
        }
      }
    ]
  },
  {
    id: 2002,
    text: 'Изучите фрагмент топографической карты и ответь на вопросы.',
    img: '2002.jpg',
    width: 500,
    height: 600,
    minZoom: 0.4,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.5,
    disabled: false,
    q: [
      {
        id: 2002001,
        label: 'На какой широте и долготе находится г. Зелёная?',
        value: '',
        placeholder: 'Градусы минуты и секунды заменяйте пробелом сокращение с.ш. в.д.',
        status: '',
        score: 1,
        answer: [
          '54 48 58 с.ш. 18 08 31 в.д.',
          '54 48 57 с.ш. 18 08 31 в.д.',
          '54 48 59 с.ш. 18 08 31 в.д.',
          '54 48 58 с.ш. 18 08 30 в.д.',
          '54 48 58 с.ш. 18 08 32 в.д.',
          '54 48 57 с.ш. 18 08 30 в.д.',
          '54 48 59 с.ш. 18 08 30 в.д.',
          '54 48 57 с.ш. 18 08 32 в.д.',
          '54 48 59 с.ш. 18 08 32 в.д.'
        ],
        class: {
          correct: false,
          inCorrect: false
        }
      }
    ]
  },
  {
    id: 2003,
    text: 'Изучите фрагмент топографической карты и ответь на вопросы.',
    img: '2003.jpg',
    width: 500,
    height: 600,
    minZoom: 0.5,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.5,
    disabled: false,
    q: [
      {
        id: 2003001,
        label: 'Чему равен магнитный азимут от оборудованного источника на дом лесника в квадрате 6611?',
        value: '',
        placeholder: '2 числа через пробел',
        status: '',
        score: 1,
        answer: ['-307 -312'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2003002,
        label: 'Чему равны географические координаты оборудованного источника?',
        value: '',
        placeholder: 'Градусы минуты и секунды заменяйте пробелом сокращение с.ш. в.д.',
        status: '',
        score: 1,
        answer: [
          '54 40 55 - 54 41 05  с.ш. 18 05 05 - 18 05 15 в.д.',
          '54 40 55-54 41 05  с.ш. 18 05 05-18 05 15 в.д.'
        ],
        class: {
          correct: false,
          incorrect: false
        }
      },
      {
        id: 2003003,
        label: 'Чему равны прямоугольные координаты оборудованного источника?',
        value: '',
        placeholder: 'числа через пробел',
        status: '',
        score: 1,
        answer: ['6066000 - 6066050 4312050 - 4312150'],
        class: {
          correct: false,
          incorrect: false
        }
      }
    ]
  },
  {
    id: 2004,
    text: 'Изучите фрагмент топографической карты и ответь на вопросы.',
    img: '2004.jpg',
    width: 500,
    height: 600,
    minZoom: 0.7,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.7,
    disabled: false,
    q: [
      {
        id: 2004001,
        label: 'Определите масштаб карты',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['карта – километровка', 'в 1 см 500 м', '1:500'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2004002,
        label: 'Откуда и куда течет вода - из озера Лебяжье в озеро Длинное или наоборот?',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: [
          'вода течет из озера лебяжье в озеро длинное',
          'из озера лебяжье в озеро длинное',
          'из лебяжье в длинное'
        ],
        class: {
          correct: false,
          incorrect: false
        }
      }
    ]
  },
  {
    id: 2005,
    text: 'Изучите фрагмент топографической карты и ответь на вопросы.',
    img: '2005.jpg',
    width: 500,
    height: 600,
    minZoom: 0.7,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.7,
    disabled: false,
    q: [
      {
        id: 2005001,
        label: 'Определите масштаб фрагмента карты',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['1:50 000', '1 к 50 000', '1 50 000'],
        class: {
          correct: false,
          inCorrect: false
        }
      }
    ]
  },
  {
    id: 2006,
    text: 'Изучите фрагмент топографической карты и ответь на вопросы.',
    img: '2006.jpg',
    width: 500,
    height: 600,
    minZoom: 0.7,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.7,
    disabled: false,
    q: [
      {
        id: 2006001,
        label: 'Определите наивысшую точку квадрата 72 66 данной карты.',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['гора с отметкой 839,1 м.'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2006002,
        label: 'Определите географические координаты наивысшей точки квадрата 72 66 данной карты.',
        value: '',
        placeholder: 'Градусы минуты и секунды заменяйте пробелом сокращение с.ш. в.д.',
        status: '',
        score: 1,
        answer: ['54 44 58 с.ш. 59 35 08 в.д.'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2006002,
        label: 'Определите прямоугольные координаты наивысшей точки квадрата 72 66 данной карты.',
        value: '',
        placeholder: 'числа через пробел',
        status: '',
        score: 1,
        answer: ['6072,5 км 10666,4 км', '6072,5 10666,4'],
        class: {
          correct: false,
          inCorrect: false
        }
      }
    ]
  },
  {
    id: 2007,
    text: 'Изучите фрагмент топографической карты и ответь на вопросы.',
    img: '2007.jpg',
    width: 500,
    height: 600,
    minZoom: 0.7,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.7,
    disabled: false,
    q: [
      {
        id: 2007001,
        label: 'Определите численный масштаб карты, используя линии километровой сетки.',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['1:25000', '1 к 25000', '1 25000'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2007002,
        label: 'Чему равна ширина р. Андога в районе брода (кв.7108)?',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['10 м'],
        class: {
          correct: false,
          inCorrect: false
        }
      }
    ]
  },
  {
    id: 2008,
    text: 'Известно, что линии меридианов проведены на карте через 2 см и расстояние на местности от точки А до точки Б составляет 4 километра.',
    img: '2008.jpg',
    width: 500,
    height: 600,
    minZoom: 0.65,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.65,
    disabled: false,
    q: [
      {
        id: 2008001,
        label: 'Определите масштаб приведенного фрагмента топографической карты.',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['1:100000', '1 к 100000', '1 100000', 'в 1 см 1000 м'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2008002,
        label: 'Определите высоту сечения рельефа (через сколько метров проведены сплошные горизонтали на карте).',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['20 м'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2008003,
        label: 'Какова ширина и глубина реки Клязьмы в центральной части карты?',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['ширина 140 м глубина 1,5 м', '140 м 1,5 м'],
        class: {
          correct: false,
          inCorrect: false
        }
      }
    ]
  },
  {
    id: 2009,
    text: 'Инцидент на картографической фабрике. Во время создания топографической карты на фрагменте в среднем течении реки Зеленой были утрачены отображения значков, а в условных обозначениях – подписи к ним. Помогите картографу восстановить заполнение карты и легенду к ней. Известно, что карта имеет километровую сетку, а значения координат объектов приведены в метрах.',
    img: '2009.jpg',
    width: 500,
    height: 600,
    minZoom: 0.7,
    maxZoom: 2,
    zoomStep: 0.1,
    zoom: 0.7,
    disabled: false,
    q: [
      {
        id: 2009001,
        label: 'Определите высоту сечения горизонталей.',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['5 м'],
        class: {
          correct: false,
          inCorrect: false
        }
      },
      {
        id: 2009002,
        label: 'Укажите другое название километровой сетки?',
        value: '',
        placeholder: 'Ответ',
        status: '',
        score: 1,
        answer: ['прямоугольная'],
        class: {
          correct: false,
          inCorrect: false
        }
      }
    ]
  }
])

function handleSubmit() {
  disableQuestion()
  questions.value[getIndex()].q.forEach((item, index) => {
    let result = item.answer.includes(item.value.toLowerCase())
    item.status = result ? 'Верно' : 'Неверно'
    item.class.correct = result
    item.class.incorrect = !result
    if (result) score.value += item.score
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
      :allow-touch-move="false"
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
            <div class="question-image">
              <map-canvas
                :image-url="`img\\${question.img}`"
                :width="question.width"
                :height="question.height"
                :min-zoom="question.minZoom"
                :max-zoom="question.maxZoom"
                :zoom-step="question.zoomStep"
                :zoom="question.zoom"
              />
            </div>
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
  width: 1300px;
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
  grid-template-rows: 2fr 8fr;
  justify-content: center;
}

.question-text {
  font-weight: bolder;
  width: 100%;
  margin-bottom: 8px;
  font-size: 100%;
  grid-column: 2;
  grid-row: 1;
}

.question-controls {
  grid-column: 2;
  grid-row: 2;
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
