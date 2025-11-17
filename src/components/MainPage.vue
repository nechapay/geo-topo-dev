<script setup>
import { computed, ref, reactive, watch } from 'vue'

const emits = defineEmits(['ended'])

const questions = []

const blocks = ref([
  {
    id: 1,
    name: 'Block1',
    active: true,
    action: showBlock
  },
  {
    id: 2,
    name: 'Block2',
    active: false,
    action: showBlock
  },
  {
    id: 3,
    name: 'Block3',
    active: false,
    action: showBlock
  },
  {
    id: 4,
    name: 'Block4',
    active: false,
    action: showBlock
  }
])
const caption = ref('')

const blockVisibility = ref([true, false, false, false])

function showBlock(block) {
  for (let i = 0; i < blockVisibility.value.length; i++) {
    blockVisibility.value[i] = false
    blocks.value[i].active = false
  }
  blockVisibility.value[block] = true
  blocks.value[block].active = true
  caption.value = block
  console.log(blockVisibility.value)
}
</script>
<template>
  <div class="my-grid fill">
    <div class="nav-header">
      <h1 class="nav-title">Топография</h1>
      <vr></vr>
      <div class="base-flex nav-buttons-container">
        <a
          v-for="block in blocks"
          :key="block.id"
          @click="block.action(block.id - 1)"
          class="nav-button"
          :class="{ active: block.active }"
          >{{ block.name }}</a
        >
      </div>
    </div>
    <div class="page-body">
      {{ caption }}
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
  gap: 0.1%;
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
  background-image: linear-gradient(rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.3)), url('/img/bg3.jpg');
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
}

.nav-button {
  margin: 0 8px;
  color: black;
  font-size: 24px;
  transition-duration: 0.5s;
  cursor: pointer;
  padding: 0 4px 0 8px;
  text-transform: uppercase;
}

.nav-button.active,
.nav-button:hover {
  color: red;
  text-decoration: underline;
}
</style>
