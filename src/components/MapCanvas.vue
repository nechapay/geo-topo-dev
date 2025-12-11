<template>
  <div
    class="canvas-container base-flex"
    @wheel="handleWheel"
    @mousedown="startDrag"
    @mousemove="handleDrag"
    @mouseup="stopDrag"
    @mouseleave="stopDrag"
  >
    <canvas ref="canvasRef" :width="width" :height="height"></canvas>

    <div class="controls">
      <button @click="resetView">Сброс</button>
      <button @click="zoomIn">+</button>
      <button @click="zoomOut">-</button>
      <span>Масштаб: {{ (zoom * 100).toFixed(0) }}%</span>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch, computed } from 'vue'

const props = defineProps({
  imageUrl: {
    type: String,
    required: true
  },
  width: {
    type: Number,
    default: 800
  },
  height: {
    type: Number,
    default: 600
  },
  minZoom: {
    type: Number,
    default: 0.1
  },
  maxZoom: {
    type: Number,
    default: 5
  },
  zoomStep: {
    type: Number,
    default: 0.1
  }
})

const canvasRef = ref(null)
const image = ref(null)
const isDragging = ref(false)
const lastMousePos = ref({ x: 0, y: 0 })

const viewport = ref({
  x: 0,
  y: 0,
  zoom: 0.15
})

const zoom = computed(() => viewport.value.zoom)
const position = computed(() => ({ x: viewport.value.x, y: viewport.value.y }))

onMounted(() => {
  loadImage()
})

watch(
  viewport,
  () => {
    drawCanvas()
  },
  { deep: true }
)

const loadImage = () => {
  image.value = new Image()
  image.value.onload = () => {
    centerImage()
    drawCanvas()
  }
  image.value.src = props.imageUrl
}

const centerImage = () => {
  if (!image.value || !canvasRef.value) return

  const canvas = canvasRef.value
  viewport.value.x = (canvas.width - image.value.width * viewport.value.zoom) / 2
  viewport.value.y = (canvas.height - image.value.height * viewport.value.zoom) / 2
}

const drawCanvas = () => {
  if (!canvasRef.value || !image.value) return

  const canvas = canvasRef.value
  const ctx = canvas.getContext('2d')

  ctx.clearRect(0, 0, canvas.width, canvas.height)

  drawGrid(ctx)

  ctx.save()

  ctx.translate(viewport.value.x, viewport.value.y)
  ctx.scale(viewport.value.zoom, viewport.value.zoom)

  ctx.drawImage(image.value, 0, 0)

  ctx.restore()
}

const drawGrid = (ctx) => {
  const canvas = canvasRef.value
  const gridSize = 20
  const gridColor = '#f0f0f0'

  ctx.strokeStyle = gridColor
  ctx.lineWidth = 1

  for (let x = 0; x <= canvas.width; x += gridSize) {
    ctx.beginPath()
    ctx.moveTo(x, 0)
    ctx.lineTo(x, canvas.height)
    ctx.stroke()
  }

  for (let y = 0; y <= canvas.height; y += gridSize) {
    ctx.beginPath()
    ctx.moveTo(0, y)
    ctx.lineTo(canvas.width, y)
    ctx.stroke()
  }
}

const handleWheel = (event) => {
  event.preventDefault()

  const delta = event.deltaY > 0 ? -props.zoomStep : props.zoomStep
  const newZoom = Math.max(props.minZoom, Math.min(props.maxZoom, viewport.value.zoom + delta))

  const rect = canvasRef.value.getBoundingClientRect()
  const mouseX = event.clientX - rect.left
  const mouseY = event.clientY - rect.top

  const zoomFactor = newZoom / viewport.value.zoom
  viewport.value.x = mouseX - (mouseX - viewport.value.x) * zoomFactor
  viewport.value.y = mouseY - (mouseY - viewport.value.y) * zoomFactor

  viewport.value.zoom = newZoom
}

const zoomIn = () => {
  viewport.value.zoom = Math.min(props.maxZoom, viewport.value.zoom + props.zoomStep)
}

const zoomOut = () => {
  viewport.value.zoom = Math.max(props.minZoom, viewport.value.zoom - props.zoomStep)
}

const resetView = () => {
  viewport.value = {
    x: 0,
    y: 0,
    zoom: 0.15
  }
  centerImage()
}

const startDrag = (event) => {
  if (event.button !== 0) return

  isDragging.value = true
  const rect = canvasRef.value.getBoundingClientRect()
  lastMousePos.value = {
    x: event.clientX - rect.left,
    y: event.clientY - rect.top
  }

  canvasRef.value.style.cursor = 'grabbing'
}

const handleDrag = (event) => {
  if (!isDragging.value) return

  const rect = canvasRef.value.getBoundingClientRect()
  const currentMousePos = {
    x: event.clientX - rect.left,
    y: event.clientY - rect.top
  }

  const dx = currentMousePos.x - lastMousePos.value.x
  const dy = currentMousePos.y - lastMousePos.value.y

  viewport.value.x += dx
  viewport.value.y += dy

  lastMousePos.value = currentMousePos
}

const stopDrag = () => {
  if (!isDragging.value) return

  isDragging.value = false
  canvasRef.value.style.cursor = 'grab'
}
</script>

<style scoped>
.canvas-container {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: grab;
  user-select: none;
}

canvas {
  display: block;
  background-color: #fff;
  border: 1px dashed grey;
}

.controls {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  background-color: rgba(255, 255, 255, 0.8);
  padding: 8px 16px;
  border-radius: 4px;
  display: flex;
  gap: 8px;
  align-items: center;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.controls button {
  padding: 4px 8px;
  border: 1px solid #ccc;
  background-color: #fff;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.controls button:hover {
  background-color: #f0f0f0;
}

.controls span {
  font-size: 14px;
  margin-left: 8px;
}
</style>
