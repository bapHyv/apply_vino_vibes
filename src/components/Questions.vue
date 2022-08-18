<script setup>
import { ref } from 'vue'

const props = defineProps({
  dsplInfo: { type: Object, required: true },
  toggle: { type: Function, required: true },
})

const displayData = ref([
  {
    title: 'Question n°1 pour recuperer mon cv !',
    question:
      "Quelle est la methode JS qui supprime le dernier element d'un tableau et le renvoie ?",
    inputsValues: ['push', 'shift', 'pop', 'unshift'],
  },
  {
    title: 'Question n°2 pour recuperer ma lettre de motivation !',
    question: 'Quel est le nom du dieu grec du vin et de la fete ?',
    inputsValues: ['Zeus', 'Dionysos', 'Eros', 'Poseidon'],
  },
  {
    title: 'Question n°3 pour recuperer ma lettre de recommandation !',
    question:
      'Quelle directive permet de faire du rendu conditionnel avec VueJS ?',
    inputsValues: ['v-bind', 'v-for', 'v-text', 'v-if'],
  },
  {
    title: '4eme et dernière question ! Pour recuperer mes disponibilites !',
    question: 'Le Saint-Julien est un vin de ... ?',
    inputsValues: ['Loire', 'Bourgogne', 'Bordeaux', 'Franche-comté'],
  },
])

const unsetWrongValue = (inputValue) => {
  if (inputValue != props.dsplInfo.answer) {
    props.dsplInfo.wrong = false
  }
}
</script>

<template>
  <p class="first-p">
    {{ displayData[dsplInfo.arrayIndex].title }}
  </p>
  <p class="second-p">
    {{ displayData[dsplInfo.arrayIndex].question }}
  </p>
  <div class="inputs-container">
    <div class="straight-container">
      <div
        v-for="inputValue in displayData[dsplInfo.arrayIndex].inputsValues"
        :key="inputValue"
        class="input-and-label-container"
      >
        <input
          type="radio"
          v-model="dsplInfo.answer"
          :name="inputValue"
          :id="inputValue"
          :value="inputValue"
          @click="unsetWrongValue(inputValue)"
        />
        <label class="label-text" :for="inputValue">{{ inputValue }}</label>
      </div>
    </div>
  </div>

  <div class="btn-container">
    <button @click="toggle()">Valider</button>
  </div>
</template>

<style></style>
