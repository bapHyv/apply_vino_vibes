<script setup>
import { computed, ref } from 'vue'
import FirstSlide from './components/FirstSlide.vue'
import Questions from './components/Questions.vue'
import LastSlide from './components/LastSlide.vue'

const wrong = ref(false)

const dsplInfo = ref({
  slideNb: 1,
  arrayIndex: 0,
  answer: '',
  wrong: false
})

const computedSlideNb = computed(() => dsplInfo.value.slideNb)

const validate = () => {
  dsplInfo.value.slideNb++
  dsplInfo.value.answer = ''
  dsplInfo.value.wrong = false
}

const toggle = () => {
  if (dsplInfo.value.slideNb === 1 && dsplInfo.value.answer === '') {
    validate()
  } else if (dsplInfo.value.slideNb === 2 && dsplInfo.value.answer === 'pop') {
    validate()
    dsplInfo.value.arrayIndex++
  } else if (
    dsplInfo.value.slideNb === 3 &&
    dsplInfo.value.answer === 'Dionysos'
  ) {
    validate()
    dsplInfo.value.arrayIndex++
  } else if (dsplInfo.value.slideNb === 4 && dsplInfo.value.answer === 'v-if') {
    validate()
    dsplInfo.value.arrayIndex++
  } else if (
    dsplInfo.value.slideNb === 5 &&
    dsplInfo.value.answer === 'Bordeaux'
  ) {
    validate()
  } else {
    dsplInfo.value.wrong = true
  }
}
</script>

<template>
  <Transition name="slide">
    <section v-if="dsplInfo.slideNb === 1" :class="['content-container', {wrong: dsplInfo.wrong}]">
      <FirstSlide :dsplInfo="dsplInfo" :toggle="toggle" />
    </section>
  </Transition>

  <Transition appear name="slide">
    <section v-if="dsplInfo.slideNb === 2" :class="['content-container', {wrong: dsplInfo.wrong}]">
      <Questions :dsplInfo="dsplInfo" :toggle="toggle" />
    </section>
  </Transition>

  <Transition appear name="slide">
    <section v-if="dsplInfo.slideNb === 3" :class="['content-container', {wrong: dsplInfo.wrong}]">
      <Questions :dsplInfo="dsplInfo" :toggle="toggle" />
    </section>
  </Transition>

  <Transition appear name="slide">
    <section v-if="dsplInfo.slideNb === 4" :class="['content-container', {wrong: dsplInfo.wrong}]">
      <Questions :dsplInfo="dsplInfo" :toggle="toggle" />
    </section>
  </Transition>

  <Transition appear name="slide">
    <section v-if="dsplInfo.slideNb === 5" :class="['content-container', {wrong: dsplInfo.wrong}]">
      <Questions :dsplInfo="dsplInfo" :toggle="toggle" />
    </section>
  </Transition>

  <Transition name="slide">
    <section v-if="dsplInfo.slideNb === 6" :class="['content-container', {wrong: dsplInfo.wrong}]">
      <LastSlide />
    </section>
  </Transition>
</template>

<style>
html {
  overflow: hidden;
}

.content-container {
  position: absolute;
  block-size: 60vh;
  inline-size: 50vw;
  top: 10vh;
  left: 25vw;
  margin: auto;
  padding: 20px;
  border-radius: 20px;
  box-shadow: 0px 0px 40px white;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
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
