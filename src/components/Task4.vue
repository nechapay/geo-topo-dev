<script setup>
import { computed, ref, reactive, watch, onMounted } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination, Navigation } from 'swiper/modules'

import _ from 'lodash'

import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'

const swiperInstance = ref(null)

const score = ref(0)

const onSwiper = (swiper) => {
  swiperInstance.value = swiper
}

const selected = ref([
  {
    id: '',
    value: '',
    status: false,
    points: 0
  },
  {
    id: '',
    value: '',
    status: false,
    points: 0
  },
  {
    id: '',
    value: '',
    status: false,
    points: 0
  },
  {
    id: '',
    value: '',
    status: false,
    points: 0
  },
  {
    id: '',
    value: '',
    status: false,
    points: 0
  }
])

const modules = [Pagination, Navigation]

onMounted(() => {
  questions.value.forEach((question) => {
    question.opt = _.shuffle(question.opt)
  })
})
const questions = ref([
  {
    id: 4001,
    text: 'ОПРЕДЕЛИТЬ МАСШТАБ ТОПОГРАФИЧЕСКОЙ КАРТЫ ПО ФРАГМЕНТУ, ЕСЛИ ИЗВЕСТНА СТОРОНА КВАДРАТА КИЛОМЕТРОВОЙ (КООРДИНАТНОЙ) СЕТКИ',
    redText: 'СТОРОНА КВАДРАТА 4 СМ.',
    img: '4001.png',
    disabled: false,
    opt: [
      {
        id: 4001001,
        value: 'Масштаб 1:25 000',
        status: true,
        points: 1
      },
      {
        id: 4001002,
        value: 'Масштаб 1:100 000',
        status: false,
        points: 0
      },
      {
        id: 4001003,
        value: 'Масштаб 1:50 000',
        status: false,
        points: 0
      }
    ]
  },
  {
    id: 4002,
    text: 'ОПРЕДЕЛИТЬ МАСШТАБ ТОПОГРАФИЧЕСКОЙ КАРТЫ ПО ФРАГМЕНТУ, ЕСЛИ ИЗВЕСТНА СТОРОНА КВАДРАТА КИЛОМЕТРОВОЙ (КООРДИНАТНОЙ) СЕТКИ',
    redText: 'СТОРОНА КВАДРАТА 2 СМ.',
    img: '4002.png',
    disabled: false,
    opt: [
      {
        id: 4002001,
        value: 'Масштаб 1:25 000',
        status: false,
        points: 0
      },
      {
        id: 4002002,
        value: 'Масштаб 1:100 000',
        status: false,
        points: 0
      },
      {
        id: 4002003,
        value: 'Масштаб 1:50 000',
        status: true,
        points: 1
      }
    ]
  },
  {
    id: 4003,
    text: 'ОПРЕДЕЛИТЬ МАСШТАБ ТОПОГРАФИЧЕСКОЙ КАРТЫ ПО ФРАГМЕНТУ, ЕСЛИ ИЗВЕСТНА СТОРОНА КВАДРАТА КИЛОМЕТРОВОЙ (КООРДИНАТНОЙ) СЕТКИ',
    redText: 'СТОРОНА КВАДРАТА 2 СМ.',
    img: '4003.png',
    disabled: false,
    opt: [
      {
        id: 4003001,
        value: 'Масштаб 1:25 000',
        status: false,
        points: 0
      },
      {
        id: 4003002,
        value: 'Масштаб 1:100 000',
        status: true,
        points: 1
      },
      {
        id: 4003003,
        value: 'Масштаб 1:50 000',
        status: false,
        points: 0
      }
    ]
  },
  {
    id: 4004,
    text: 'ОПРЕДЕЛИТЬ ЧИСЛЕННЫЙ, ИМЕНОВАННЫЙ И ЛИНЕЙНЫЙ МАСШТАБ ТОПОГРАФИЧЕСКОЙ КАРТЫ',
    redText: '',
    img: '4004.png',
    disabled: false,
    opt: [
      {
        id: 4004001,
        value:
          'Численный масштаб:1:50 000, Именованный масштаб:в 1 см. 500м., Линейный масштаб: Сплошные горизонтали проведены через 10 м.',
        status: true,
        points: 1
      },
      {
        id: 4004002,
        value:
          'Численный масштаб: Сплошные горизонтали проведены через 10 м., Именованный масштаб:в 1 см. 500м., Линейный масштаб: 1:50 000',
        status: false,
        points: 0
      },
      {
        id: 4004003,
        value: 'Численный масштаб: 1:50 000, Именованный масштаб:в 1 см. 500м., Линейный масштаб: 1000 м.',
        status: false,
        points: 0
      }
    ]
  },
  {
    id: 4005,
    text: 'ОПРЕДЕЛИТЬ МАСШТАБ ТОПОГРАФИЧЕСКОЙ КАРТЫ ПО РАССТОЯНИЯМ МЕЖДУ МЕСТНЫМИ ОБЪЕКТАМИ',
    redText: 'РАССТОЯНИЕ МЕЖДУ ЗНАКАМИ ПО КАРТЕ 2 СМ. СТОРОНА КВАДРАТА 2 СМ.',
    img: '4005.png',
    disabled: false,
    opt: [
      {
        id: 4005001,
        value: 'Масштаб 1:25 000',
        status: false,
        points: 0
      },
      {
        id: 4005002,
        value: 'Масштаб 1:100 000',
        status: false,
        points: 0
      },
      {
        id: 4005003,
        value: 'Масштаб 1:50 000',
        status: true,
        points: 1
      }
    ]
  }
])

function handleRadio(val) {
  disableQuestion(val.target.id)
  score.value += +selected.value[getIndex()].points
}

function disableQuestion(id) {
  questions.value[getIndex()].disabled = true
}

const getRadioOptionClass = (value) => {
  return {
    'radio-correct': selected.value[getIndex()].status,
    'radio-incorrect': selected.value[getIndex()].status === false
  }
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
        <div class="slide-content">
          <div class="question-text">{{ question.text }}</div>
          <div class="question-red-text" v-if="question.redText !== ''">{{ question.redText }}</div>
          <div class="question-image"><img :src="`img\\${question.img}`" alt="" /></div>
          <div class="controls base-flex">
            <div class="radio-group">
              <h4>ВЫБРАТЬ ПРАВИЛЬНЫЙ ВАРИАНТ</h4>
              <label v-for="item in question.opt" :key="item.id" :class="getRadioOptionClass(item.value)">
                <input
                  type="radio"
                  :id="item.id"
                  :value="item"
                  v-model="selected[swiperInstance ? swiperInstance.activeIndex : 0]"
                  @change="handleRadio"
                  :disabled="question.disabled"
                />
                <span>{{ item.value }}</span>
              </label>
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
  height: 300px;
}

.radio-group {
  max-width: 95%;
  display: flex;
  flex-direction: column;
  padding: 1%;
  border: 1px solid black;
  align-items: flex-start;
  justify-content: flex-start;
  margin-bottom: 1%;
}

label {
  display: flex;
  cursor: pointer;
  font-weight: 500;
  position: relative;
  overflow: hidden;
  margin-bottom: 0.375em;
}
label input {
  position: absolute;
  left: -9999px;
}
label input:checked + span {
  background-color: #d6d6e5;
}
label input:checked + span:before {
  box-shadow: inset 0 0 0 0.4375em #28b9e7;
}
label span {
  display: flex;
  align-items: center;
  padding: 0.375em 0.75em 0.375em 0.375em;
  border-radius: 99em;
  transition: 0.25s ease;
  font-size: 100%;
  text-align: left;
}
label span:hover {
  background-color: #d6d6e5;
}
label span:before {
  display: flex;
  flex-shrink: 0;
  content: '';
  background-color: #fff;
  width: 1.5em;
  height: 1.5em;
  border-radius: 50%;
  margin-right: 0.375em;
  transition: 0.25s ease;
  box-shadow: inset 0 0 0 0.125em #28b9e7;
}

.radio-correct input:checked + span {
  color: rgb(32, 155, 32);
}

.radio-correct input:checked + span:before {
  box-shadow: inset 0 0 0 0.4375em rgb(86, 185, 86);
}

.radio-incorrect input:checked + span {
  color: red;
}

.radio-incorrect input:checked + span:before {
  box-shadow: inset 0 0 0 0.4375em red;
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
