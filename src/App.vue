<script setup>
import { computed, ref } from 'vue'
import FirstSlide from './components/FirstSlide.vue'
import Questions from './components/Questions.vue'
import LastSlide from './components/LastSlide.vue'

const dsplInfo = ref({
  slideNb: 1,
  arrayIndex: 0,
  answer: '',
  triggerAnimation: false,
})

const computedSlideNb = computed(() => dsplInfo.value.slideNb)

const validate = () => {
  dsplInfo.value.slideNb++
  dsplInfo.value.answer = ''
  dsplInfo.value.triggerAnimation = true
  dsplInfo.value.triggerAnimation = false
  dsplInfo.value.triggerAnimation = true
}

const toggle = () => {
  if (dsplInfo.value.slideNb === 1 && dsplInfo.value.answer === '') {
    validate()
  }
  if (dsplInfo.value.slideNb === 2 && dsplInfo.value.answer === 'pop') {
    validate()
    dsplInfo.value.arrayIndex++
  }
  if (dsplInfo.value.slideNb === 3 && dsplInfo.value.answer === 'Dionysos') {
    validate()
    dsplInfo.value.arrayIndex++
  }
  if (dsplInfo.value.slideNb === 4 && dsplInfo.value.answer === 'v-if') {
    validate()
    dsplInfo.value.arrayIndex++
  }
  if (dsplInfo.value.slideNb === 5 && dsplInfo.value.answer === 'Bordeaux') {
    validate()
  }
}
</script>

<template>
  <Transition name="slide">
    <section v-if="dsplInfo.slideNb === 1" class="content-container">
      <FirstSlide :dsplInfo="dsplInfo" :validate="validate" :toggle="toggle" />
    </section>
  </Transition>

  <Transition appear name="slide">
    <section v-if="dsplInfo.slideNb === 2" class="content-container">
      <Questions :dsplInfo="dsplInfo" :validate="validate" :toggle="toggle" />
    </section>
  </Transition>

  <Transition appear name="slide">
    <section v-if="dsplInfo.slideNb === 3" class="content-container">
      <Questions :dsplInfo="dsplInfo" :validate="validate" :toggle="toggle" />
    </section>
  </Transition>

  <Transition appear name="slide">
    <section v-if="dsplInfo.slideNb === 4" class="content-container">
      <Questions :dsplInfo="dsplInfo" :validate="validate" :toggle="toggle" />
    </section>
  </Transition>

  <Transition appear name="slide">
    <section v-if="dsplInfo.slideNb === 5" class="content-container">
      <Questions :dsplInfo="dsplInfo" :validate="validate" :toggle="toggle" />
    </section>
  </Transition>

  <Transition name="slide">
    <section v-if="dsplInfo.slideNb === 6" class="content-container">
      <LastSlide />
    </section>
  </Transition>
</template>

<style>
html {
  overflow: hidden;
}

.btn-container {
  width: 10vw;
  margin: auto;
  display: flex;
  justify-content: space-between;
}

.content-container {
  position: absolute;
  block-size: 60vh;
  inline-size: 50vw;
  left: 25vw;
  margin: auto;
  border: 1px solid black;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.5s ease-in-out;
}

.slide-enter-from {
  transform: translateX(1000px);
  opacity: 0;
}

.slide-leave-to {
  transform: translateX(-1000px);
  opacity: 0;
}
</style>
