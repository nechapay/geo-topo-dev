<script setup>
import { computed, ref, reactive, watch, onMounted } from 'vue'

import MapCanvas from './MapCanvas.vue'

import Task1 from './Task1.vue'
import Task2 from './Task2.vue'
import Task3 from './Task3.vue'
import Task4 from './Task4.vue'
import Task5 from './Task5.vue'
import Task6 from './Task6.vue'

const emits = defineEmits(['ended'])

const blocks = ref([
  {
    id: 1,
    name: 'Карта',
    subname: 'теория',
    active: true,
    action: showBlock
  },
  {
    id: 2,
    name: 'Карта',
    subname: 'практика',
    active: false,
    action: showBlock
  },
  {
    id: 3,
    name: 'МАСШТАБ',
    subname: 'теория',
    active: false,
    action: showBlock
  },
  {
    id: 4,
    name: 'МАСШТАБ',
    subname: 'практика',
    active: false,
    action: showBlock
  },
  {
    id: 5,
    name: 'Условные знаки',
    subname: 'теория',
    active: false,
    action: showBlock
  },
  {
    id: 6,
    name: 'Условные знаки',
    subname: 'практика',
    active: false,
    action: showBlock
  }
])
const caption = ref('0')

const blockVisibility = ref([true, false, false, false, false, false])

function showBlock(block) {
  for (let i = 0; i < blockVisibility.value.length; i++) {
    blockVisibility.value[i] = false
    blocks.value[i].active = false
  }
  blockVisibility.value[block] = true
  blocks.value[block].active = true
  caption.value = block
}
</script>
<template>
  <div class="my-grid fill">
    <div class="nav-header">
      <h1 class="nav-title">Топография</h1>
      <div class="base-flex nav-buttons-container">
        <a
          v-for="block in blocks"
          :key="block.id"
          @click="block.action(block.id - 1)"
          class="nav-button"
          :class="{ active: block.active }"
          ><div class="btn-name-container">
            <p class="btn-name">{{ block.name }}</p>
            <p class="btn-subname">{{ block.subname }}</p>
          </div></a
        >
      </div>
    </div>
    <div class="page-body fill">
      <div v-if="blockVisibility[0]" class="base-flex fill">
        <map-canvas
          image-url="img\1001.jpg"
          :width="500"
          :height="600"
          :min-zoom="0.1"
          :max-zoom="2"
          :zoom-step="0.1"
          :zoom="0.15"
        />
        <task1 />
      </div>
      <task2 v-else-if="blockVisibility[1]" />
      <task3 v-else-if="blockVisibility[2]" />
      <task4 v-else-if="blockVisibility[3]" />
      <task5 v-else-if="blockVisibility[4]" />
      <task6 v-else-if="blockVisibility[5]" />
    </div>
  </div>
</template>

<style scoped>
.main-container {
  /* background: rgba(99, 35, 35, 0.493); */
  padding: 1% 1% 1.5% 1%;
  background-image: linear-gradient(rgba(255, 255, 255, 0.4), rgba(255, 255, 255, 0.6)), url('/img/bg.jpg');
  background-repeat: no-repeat;
  background-size: cover;
}

.my-grid {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr 6fr;
}

.controls-container {
  position: fixed;
  right: 0;
  bottom: 0;
  transform: translate(-50%, -15%);
}

.start-button {
  border-radius: 50%;
  height: 120px;
  font-size: 5rem;
}

.nav-header {
  background-color: rgb(117, 187, 134);
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-image: linear-gradient(rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.3)), url('/img/bg3.png');
  background-repeat: no-repeat;
  background-size: cover;
}

.nav-title {
  margin-bottom: auto;
  text-transform: uppercase;
  font-size: 400%;
  font-weight: bolder;
  color: rgb(82 106 201);
  -webkit-text-stroke: 1px #8b97ff;
}

.page-body {
  background-color: white;
  width: 100%;
}

.nav-buttons-container {
  background: #c1e8ff;
  border-radius: 8px 8px 0 0;
  border-width: 1px 1px 0 1px;
  border-color: grey;
  border-style: solid;
}

.nav-button {
  /* margin: 0 8px; */
  color: black;
  transition-duration: 0.5s;
  cursor: pointer;
  padding: 0 4px 0 8px;
  background: #c1e8ff;
}

.nav-button:first-child {
  border-radius: 8px 0 0 0;
}

.nav-button:last-child {
  border-radius: 0 8px 0 0;
}

.nav-button.active,
.nav-button:hover {
  color: rgb(75, 86, 187);
  background: white;
}

.block-content-container {
  display: grid;
  grid-template-columns: 1fr 6fr 1fr;
  grid-template-rows: 1fr;
}

.navigate-left,
.navigate-right {
  height: 100%;
  background: green;
}
.block-content {
  height: 100%;
}

.btn-name {
  text-transform: uppercase;
  font-size: 24px;
  margin-bottom: -16px;
}

.btn-subname {
  font-size: 16px;
  text-transform: lowercase;
  color: grey;
}
</style>
