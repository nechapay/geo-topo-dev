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
    id: 6001,
    text: '',
    redText: '',
    img: '6001.png',
    disabled: false,
    opt: [
      {
        id: 6001001,
        value: 'ШИРИНА РЕКИ 250м., ГЛУБИНА 4.8м. ХАРАКТЕР ГРУНТА ДНА - ПЕСОК',
        status: true,
        points: 1
      },
      {
        id: 6001002,
        value: 'ШИРИНА РЕКИ 4.8м., ГЛУБИНА 250м. ХАРАКТЕР ГРУНТА ДНА - ПОЧВА',
        status: false,
        points: 0
      },
      {
        id: 6001003,
        value: 'ШИРИНА РЕКИ 250м.,  ГЛУБИНА 4.8м. ХАРАКТЕР ГРУНТА ДНА - ПЛАВУН',
        status: false,
        points: 0
      }
    ]
  },
  {
    id: 6002,
    text: '',
    redText: '',
    img: '6002.png',
    disabled: false,
    opt: [
      {
        id: 6002001,
        value: 'НАПРАВЛЕНИЕ ТЕЧЕНИЯ РЕКИ - НА ЮГ. СКОРОСТЬ ТЕЧЕНИЯ 0,1 км/ч',
        status: false,
        points: 0
      },
      {
        id: 6002002,
        value: 'НАПРАВЛЕНИЕ ТЕЧЕНИЯ РЕКИ - НА ЮГО-ВОСТОК. СКОРОСТЬ ТЕЧЕНИЯ 0,1 км/сек.',
        status: false,
        points: 0
      },
      {
        id: 6002003,
        value: 'НАПРАВЛЕНИЕ ТЕЧЕНИЯ РЕКИ - НА ЮГО-ВОСТОК. СКОРОСТЬ ТЕЧЕНИЯ 0,1 м/сек.',
        status: true,
        points: 1
      }
    ]
  },
  {
    id: 6003,
    text: '',
    redText: '',
    img: '6003.png',
    disabled: false,
    opt: [
      {
        id: 6003001,
        value: 'МАКСИМАЛЬНАЯ ВЫСОТА ПОДЪЕМА ВОДЫ 108.9см.',
        status: false,
        points: 0
      },
      {
        id: 6003002,
        value: 'ОТМЕТКА УРЕЗА ВОДЫ 108.9м. НАД УРОВНЕМ МОРЯ',
        status: true,
        points: 1
      },
      {
        id: 6003003,
        value: 'ШИРИНА РЕКИ 108.9м.',
        status: false,
        points: 0
      }
    ]
  },
  {
    id: 6004,
    text: '',
    redText: '',
    img: '6004.png',
    disabled: false,
    opt: [
      {
        id: 6006001,
        value: 'ШИРИНА РЕКИ 40 м. ГЛУБИНА 2.1 м. ХАРАКТЕР ГРУНТА ДНА-ПЕСОК',
        status: true,
        points: 1
      },
      {
        id: 6006002,
        value: 'ГЛУБИНА 4.0 м. ШИРИНА РЕКИ 2,1 м. ХАРАКТЕР ГРУНТА ДНА-ПОЧВА',
        status: false,
        points: 0
      },
      {
        id: 6006003,
        value: 'ДЛИНА РЕКИ 40 км.  ГЛУБИНА 2.1 м. ХАРАКТЕР ГРУНТА ДНА-ПЕСОК',
        status: false,
        points: 0
      }
    ]
  },
  {
    id: 6005,
    text: '',
    redText: '',
    img: '6005.png',
    disabled: false,
    opt: [
      {
        id: 6005001,
        value: 'КОЛОДЕЦ',
        status: false,
        points: 0
      },
      {
        id: 6005002,
        value: 'ВОДОПАД',
        status: false,
        points: 0
      },
      {
        id: 6005003,
        value: 'ИСТОЧНИК (КЛЮЧ, РОДНИК)',
        status: true,
        points: 1
      }
    ]
  },
  {
    id: 6006,
    text: '',
    redText: '',
    img: '6006.png',
    disabled: false,
    opt: [
      { id: 6006001, value: 'ПРОХОДИМОЕ БОЛОТО, ГЛУБИНА 0,8м.', status: false, points: 0 },
      { id: 6006002, value: 'СОЛОНЧАК, ТОЛЩИНА СЛОЯ СОЛИ 0,8м.', status: false, points: 0 },
      { id: 6006003, value: 'НЕПРОХОДИМОЕ БОЛОТО, ГЛУБИНА 0,8м.', status: true, points: 1 }
    ]
  },
  {
    id: 6007,
    text: '',
    redText: '',
    img: '6007.png',
    disabled: false,
    opt: [
      {
        id: 6007001,
        value: 'БРОД. ДЛИНА 0.5м. ШИРИНА 10м. ХАРАКТЕР ГРУНТА ДНА-ТИНА, СКОРОСТЬ ТЕЧЕНИЯ 0,1 м/сек.',
        status: false,
        points: 0
      },
      {
        id: 6007002,
        value: 'БРОД. ГЛУБИНА 0.5м. ДЛИНА 10м. ХАРАКТЕР ГРУНТА ДНА-ТИНА, СКОРОСТЬ ТЕЧЕНИЯ 0,1 км/ч',
        status: false,
        points: 0
      },
      {
        id: 6007003,
        value: 'БРОД. ГЛУБИНА 0.5м. ДЛИНА 10м. ХАРАКТЕР ГРУНТА ДНА-ТВЕРДЫЙ, СКОРОСТЬ ТЕЧЕНИЯ 0,1 м.сек.',
        status: true,
        points: 1
      }
    ]
  },
  {
    id: 6008,
    text: '',
    redText: '',
    img: '6008.png',
    disabled: false,
    opt: [
      {
        id: 6008001,
        value: 'МОСТ. МАТЕРИАЛ-КИРПИЧ, ДЛИНА 30 м. ШИРИНА 8 м. ГРУЗОПОДЪЕМНОСТЬ 8 т.',
        status: false,
        points: 0
      },
      {
        id: 6008002,
        value: 'МОСТ. МАТЕРИАЛ-КАМЕНЬ, ВЫСОТА 30 м. ДЛИНА 8 м. ГРУЗОПОДЪЕМНОСТЬ 8 т.',
        status: false,
        points: 0
      },
      {
        id: 6008003,
        value: 'МОСТ. МАТЕРИАЛ-КАМЕНЬ, ДЛИНА 30 м. ШИРИНА 8 м. ГРУЗОПОДЪЕМНОСТЬ 8 т.',
        status: true,
        points: 1
      }
    ]
  },
  {
    id: 6009,
    text: '',
    redText: '',
    img: '6009.png',
    disabled: false,
    opt: [
      { id: 6009001, value: 'КЛЮЧ ГОРНЫЙ, ГУБИНА 5 м.', status: false, points: 0 },
      { id: 6009002, value: 'РОДНИК, ГЛУБИНА 5 м.', status: false, points: 0 },
      { id: 6009003, value: 'КОЛОДЕЦ С ВЕТРЯНЫМ ДВИГАТЕЛЕМ. ГЛУБИНА 5 м.', status: true, points: 1 }
    ]
  },
  {
    id: 6010,
    text: '',
    redText: '',
    img: '6010.png',
    disabled: false,
    opt: [
      { id: 6010001, value: 'БОЛОТО НЕПРОХОДИМОЕ, ГЛУБИНА 0,5 м.', status: false, points: 0 },
      { id: 6010002, value: 'УКАЗАТЕЛЬ ПРОХОДА, ШИРИНА 5 м.', status: false, points: 0 },
      { id: 6010003, value: 'БОЛОТО ПРОХОДИМОЕ, ГЛУБИНА 0,5 м.', status: true, points: 1 }
    ]
  },
  {
    id: 6011,
    text: '',
    redText: '',
    img: '6011.png',
    disabled: false,
    opt: [
      {
        id: 6011001,
        value: 'АВТОМОБИЛЬНАЯ ДОРОГА. ДЛИНА 13 км.  ШИРИНА 17 м. МАТЕРИАЛ ПОКРЫТИЯ-АСФАЛЬТ',
        status: false,
        points: 0
      },
      {
        id: 6011002,
        value: 'АВТОМОБИЛЬНАЯ ДОРОГА. ШИРИНА 13 м. ДЛИНА 17 км. МАТЕРИАЛ ПОКРЫТИЯ-АСФАЛЬТ',
        status: false,
        points: 0
      },
      {
        id: 6011003,
        value: 'АВТОМОБИЛЬНАЯ ДОРОГА. ШИРИНА ПОКРЫТИЯ 13 м. ОБЩАЯ ШИРИНА 17 м. МАТЕРИАЛ ПОКРЫТИЯ-АСФАЛЬТ',
        status: true,
        points: 1
      }
    ]
  },
  {
    id: 6012,
    text: '',
    redText: '',
    img: '6012.png',
    disabled: false,
    opt: [
      { id: 6012001, value: 'НАСЫПЬ ВЫСОТОЙ 2 м.', status: false, points: 0 },
      { id: 6012002, value: 'ТУННЕЛЬ ДЛИНОЙ 2 м.', status: false, points: 0 },
      { id: 6012003, value: 'ВЫЕМКА ГЛУБИНОЙ 2 м.', status: true, points: 1 }
    ]
  },
  {
    id: 6013,
    text: '',
    redText: '',
    img: '6013.png',
    disabled: false,
    opt: [
      { id: 6013001, value: 'РЕДКОЛЕСЬЕ', status: false, points: 0 },
      { id: 6013002, value: 'БУРЕЛОМ', status: false, points: 0 },
      { id: 6013003, value: 'КУСТАРНИК', status: true, points: 1 }
    ]
  },
  {
    id: 6014,
    text: '',
    redText: '',
    img: '6014.png',
    disabled: false,
    opt: [
      { id: 6014001, value: 'ОВРАГ. ДЛИНА 32 м. ГЛУБИНА 2 м.', status: false, points: 0 },
      { id: 6014002, value: 'ОВРАГ. ДЛИНА 32 м. КЛАСС ОПАСНОСТИ 2.', status: false, points: 0 },
      { id: 6014003, value: 'ОВРАГ. ШИРИНА 32 м. ГЛУБИНА 2 м.', status: true, points: 1 }
    ]
  },
  {
    id: 6015,
    text: '',
    redText: '',
    img: '6015.png',
    disabled: false,
    opt: [
      {
        id: 6015001,
        value:
          'ЛЕС СМЕШАННЫЙ. ПРЕОБЛАДАЕТ СОСНА И БЕРЁЗА. СРЕДНЯЯ ВЫСОТА 5 м. ТОЛЩИНА СТВОЛА 0,30 м. РАССТОЯНИЕ МЕЖДУ ДЕРЕВЬЯМИ 25 м.',
        status: false,
        points: 0
      },
      {
        id: 6015002,
        value:
          'ЛЕС СМЕШАННЫЙ. ПРЕОБЛАДАЕТ СОСНА И БЕРЁЗА. СРЕДНЯЯ ВЫСОТА 30 м. ТОЛЩИНА СТВОЛА 25 см. РАССТОЯНИЕ МЕЖДУ ДЕРЕВЬЯМИ 5 м.',
        status: false,
        points: 0
      },
      {
        id: 6015003,
        value:
          'ЛЕС СМЕШАННЫЙ. ПРЕОБЛАДАЕТ СОСНА И БЕРЁЗА. СРЕДНЯЯ ВЫСОТА 25 м. ТОЛЩИНА СТВОЛА 0,30 м. РАССТОЯНИЕ МЕЖДУ ДЕРЕВЬЯМИ 5 м.',
        status: true,
        points: 1
      }
    ]
  },
  {
    id: 6016,
    text: '',
    redText: '',
    img: '6016.png',
    disabled: false,
    opt: [
      { id: 6016001, value: 'ДОМ ЛЕСНИКА НА ВЫСОТЕ 159.7', status: false, points: 0 },
      { id: 6016002, value: 'ВОДОНАПОРНАЯ БАШНЯ НА ВЫСОТЕ 159.7', status: false, points: 0 },
      { id: 6016003, value: 'ТРИГОПУНКТ НА КУРГАНЕ. ОТМЕТКА 159.7', status: true, points: 1 }
    ]
  },
  {
    id: 6017,
    text: '',
    redText: '',
    img: '6017.png',
    disabled: false,
    opt: [
      { id: 6017001, value: 'БУРЕЛОМ', status: false, points: 0 },
      { id: 6017002, value: 'КУСТАРНИК', status: false, points: 0 },
      { id: 6017003, value: 'РЕДКОЛЕСЬЕ', status: true, points: 1 }
    ]
  },
  {
    id: 6018,
    text: '',
    redText: '',
    img: '6018.png',
    disabled: false,
    opt: [
      { id: 6018001, value: 'ТРИГОПУНКТ', status: false, points: 0 },
      { id: 6018002, value: 'ДОМ', status: false, points: 0 },
      { id: 6018003, value: 'ОТДЕЛЬНЫЙ ДВОР', status: true, points: 1 }
    ]
  },
  {
    id: 6019,
    text: '',
    redText: '',
    img: '6019.png',
    disabled: false,
    opt: [
      { id: 6019001, value: 'ДОМ НА ВЫСОТЕ 171.8', status: false, points: 0 },
      { id: 6019002, value: 'МЕЛЬНИЦА НА ВЫСОТЕ 171.8', status: false, points: 0 },
      { id: 6019003, value: 'ТРИГОПУНКТ ОТМЕТКА 171.8', status: true, points: 1 }
    ]
  },
  {
    id: 6020,
    text: '',
    redText: '',
    img: '6020.png',
    disabled: false,
    opt: [
      { id: 6020001, value: 'ЗАРОСЛИ КАМЫША', status: false, points: 0 },
      { id: 6020002, value: 'ЛЕС', status: false, points: 0 },
      { id: 6020003, value: 'ФРУКТОВЫЕ САДЫ', status: true, points: 1 }
    ]
  },
  {
    id: 6021,
    text: '',
    redText: '',
    img: '6021.png',
    disabled: false,
    opt: [
      { id: 6021001, value: 'ВЫЕМКА ГЛУБИНОЙ 2 м.', status: false, points: 0 },
      { id: 6021002, value: 'ДАМБА', status: false, points: 0 },
      { id: 6021003, value: 'НАСЫПЬ ВЫСОТА 2 м. ТРУБА ВОДООТВЕДЕНИЯ ПОД ДОРОГОЙ', status: true, points: 1 }
    ]
  },
  {
    id: 6022,
    text: '',
    redText: '',
    img: '6022.png',
    disabled: false,
    opt: [
      { id: 6022001, value: 'ОВРАГ. ДЛИНА 12 м.', status: false, points: 0 },
      { id: 6022002, value: 'ХОЛМ. ВЫСОТА 12 м.', status: false, points: 0 },
      { id: 6022003, value: 'ОВРАГ. ГЛУБИНА 12 м.', status: true, points: 1 }
    ]
  },
  {
    id: 6023,
    text: '',
    redText: '',
    img: '6023.png',
    disabled: false,
    opt: [
      { id: 6023001, value: 'РЕДКОЛЕСЬЕ', status: false, points: 0 },
      { id: 6023002, value: 'КУСТАРНИК', status: false, points: 0 },
      { id: 6023003, value: 'ВЫРУБКА', status: true, points: 1 }
    ]
  },
  {
    id: 6024,
    text: '',
    redText: '',
    img: '6024.png',
    disabled: false,
    opt: [
      { id: 6024001, value: 'ЛЕСНОЙ МАССИВ', status: false, points: 0 },
      { id: 6024002, value: 'ЛЕСНАЯ БАЗА ОТДЫХА', status: false, points: 0 },
      { id: 6024003, value: 'ДОМ ЛЕСНИКА', status: true, points: 1 }
    ]
  },
  {
    id: 6025,
    text: '',
    redText: '',
    img: '6025.png',
    disabled: false,
    opt: [
      { id: 6025001, value: 'РОЩА', status: false, points: 0 },
      { id: 6025002, value: 'ЛИСТВЕННЫЙ ЛЕС', status: false, points: 0 },
      { id: 6025003, value: 'ОТДЕЛЬНО СТОЯЩЕЕ ЛИСТВЕННОЕ ДЕРЕВО', status: true, points: 1 }
    ]
  },
  {
    id: 6026,
    text: '',
    redText: '',
    img: '6026.png',
    disabled: false,
    opt: [
      { id: 6026001, value: 'РАЗВАЛИНЫ', status: false, points: 0 },
      { id: 6026002, value: 'БУРЕЛОМ', status: false, points: 0 },
      { id: 6026003, value: 'КАМНИ', status: true, points: 1 }
    ]
  },
  {
    id: 6027,
    text: '',
    redText: '',
    img: '6027.png',
    disabled: false,
    opt: [
      { id: 6027001, value: 'НАСЫПЬ', status: false, points: 0 },
      { id: 6027002, value: 'ВЫЕМКА', status: false, points: 0 },
      { id: 6027003, value: 'ТРУБА ВОДООТВЕДЕНИЯ ПОД ДОРОГОЙ', status: true, points: 1 }
    ]
  },
  {
    id: 6028,
    text: '',
    redText: '',
    img: '6028.png',
    disabled: false,
    opt: [
      { id: 6028001, value: 'КУРГАННАЯ ПЕЩЕРА ГЛУБИНА 2 м.', status: false, points: 0 },
      { id: 6028002, value: 'ВОДЯНАЯ МЕЛЬНИЦА НА КУРГАНЕ', status: false, points: 0 },
      { id: 6028003, value: 'КУРГАН. ВЫСОТА 2 м.', status: true, points: 1 }
    ]
  },
  {
    id: 6029,
    text: '',
    redText: '',
    img: '6029.png',
    disabled: false,
    opt: [
      { id: 6029001, value: 'ПОЛЕВАЯ (ЛЕСНАЯ) ДОРОГА ДЛИНА 4 км.', status: false, points: 0 },
      { id: 6029002, value: 'АВТОМОБИЛЬНАЯ ДОРОГА ДЛИНА 4 км.', status: false, points: 0 },
      { id: 6029003, value: 'ПОЛЕВАЯ (ЛЕСНАЯ ДОРОГА) ШИРИНА 4 м.', status: true, points: 1 }
    ]
  },
  {
    id: 6030,
    text: '',
    redText: '',
    img: '6030.png',
    disabled: false,
    opt: [
      { id: 6030001, value: 'ВЫЕМКА. ГЛУБИНА 2 м.', status: false, points: 0 },
      { id: 6030002, value: 'ОБРЫВ. ГЛУБИНА 2 м.', status: false, points: 0 },
      { id: 6030003, value: 'НАСЫПЬ. ВЫСОТА 2 м.', status: true, points: 1 }
    ]
  }
])

// watch(
//   questions,
//   () => {
//     if (swiperInstance) {
//       swiperInstance.update() // Update Swiper after items change
//     }
//   },
//   { deep: true }
// )

function handleRadio(val) {
  disableQuestion(val.target.id)
  score.value += +selected.value[getIndex()].points
  console.log('score ', score.value)
}

function disableQuestion(id) {
  questions.value[getIndex()].disabled = true
  // questions.value.forEach((item, index) => {
  //   item.opt[0].forEach((opt) => {
  //     if (opt.id == id) {

  //       return
  //     }
  //   })
  // })
}

const getRadioOptionClass = (value) => {
  console.log('index', getIndex())
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
  width: fit-content;
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
