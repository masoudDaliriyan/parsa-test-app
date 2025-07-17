<template>
  <div dir="ltr" :key="localRating.value">
    {{ localRating.value }}
    <div class="star-group" @mouseleave="localHover = null" :class="{ disabled: props.isDisabled }">
      <div
        v-for="i in maxStars"
        :key="i"
        class="star"
        @mousemove="(e) => handleMouseMove(i, e)"
        @click="handleClick"
        :style="props.isDisabled ? 'pointer-events: none; opacity: 0.5;' : ''"
      >
        <svg
          viewBox="0 0 32 33"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
        >
          <defs>
            <linearGradient :id="'grad-' + uid + '-' + i" x1="0" y1="0" x2="1" y2="0">
              <stop offset="0%" stop-color="#F3B209" />
              <stop :offset="getOffset(i)" stop-color="#F3B209" />
              <stop :offset="getOffset(i)" stop-color="#E0E0E0" />
              <stop offset="100%" stop-color="#E0E0E0" />
            </linearGradient>
          </defs>
          <path
            :fill="'url(#grad-' + uid + '-' + i + ')'"
            d="M30.4574 13.7126L24.2284 19.7846L25.6994 28.3606C25.7309 28.5445 25.7104 28.7336 25.64 28.9064C25.5697 29.0792 25.4524 29.2289 25.3015 29.3386C25.1505 29.4482 24.9719 29.5135 24.7858 29.5269C24.5997 29.5404 24.4136 29.5015 24.2484 29.4146L16.5464 25.3656L8.84541 29.4136C8.68026 29.5005 8.49412 29.5394 8.30802 29.5259C8.12193 29.5125 7.9433 29.4472 7.79234 29.3376C7.64138 29.2279 7.52411 29.0782 7.45379 28.9054C7.38347 28.7326 7.3629 28.5435 7.39441 28.3596L8.86541 19.7836L2.63541 13.7126C2.50169 13.5823 2.40711 13.4172 2.36238 13.236C2.31765 13.0547 2.32455 12.8646 2.38231 12.687C2.44007 12.5095 2.54637 12.3517 2.68919 12.2314C2.832 12.1112 3.00563 12.0333 3.19041 12.0066L11.7994 10.7566L15.6494 2.95463C15.9864 2.27163 17.1064 2.27163 17.4434 2.95463L21.2934 10.7566L29.9024 12.0066C30.0868 12.034 30.2598 12.1122 30.4022 12.2326C30.5445 12.3529 30.6505 12.5106 30.7081 12.6878C30.7658 12.865 30.7729 13.0548 30.7286 13.2359C30.6843 13.4169 30.5904 13.582 30.4574 13.7126Z"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import { nextTick } from 'vue'


const props = defineProps({
  modelValue: {
    type: Number,
    default: 3.7
  },
  maxStars: {
    type: Number,
    default: 5
  },
  isDisabled: {
    type: Boolean,
    default: false
  }
})

const emit = defineEmits(['update:modelValue'])

const uid = Math.random().toString(36).substring(2, 9)
const localHover = ref(null)
const localRating = ref(props.modelValue)

// 🔁 Watch for changes from parent and sync local state
watch(() => props.modelValue, async (newVal) => {
  localRating.value = newVal
    await nextTick()

})

function updateHover(starIndex, e) {
  const rect = e.currentTarget.getBoundingClientRect()
  const relX = e.clientX - rect.left
  const percentage = relX / rect.width
  localHover.value = Math.min(starIndex - 1 + percentage, props.maxStars)
}

function getOffset(i) {
  const value = localHover.value ?? localRating.value
  const fill = Math.max(0, Math.min(1, value - (i - 1)))
  return `${fill * 100}%`
}

function setRating() {
  if (localHover.value !== null) {
    localRating.value = localHover.value
    emit('update:modelValue', localHover.value)
  }
}

function handleMouseMove(i, e) {
  if (props.isDisabled) return;
  updateHover(i, e);
}

function handleClick() {
  if (props.isDisabled) return;
  setRating();
}
</script>

<style scoped>
.star-group {
  display: flex;
  gap: 2px;
}
.star {
  width: 32px;
  height: 33px;
  cursor: pointer;
}
.star-group.disabled {
  pointer-events: none;
  opacity: 0.5;
}
</style>