<script setup>
import { ref } from 'vue'

const props = defineProps({
  dsplInfo: { type: Object, required: true },
  validate: { type: Function, required: true },
  toggle: { type: Function, required: true },
})

const displayData = ref([
  {
    title:
      'SUPER !! Vous avez donc envie de faire ce quiz ! 1ère question pour récupérer mon CV !',
    question:
      "Quelle est la méthode JS qui supprime le dernier élément d'un tableau et le renvoie ?",
    inputsValues: ['push', 'shift', 'pop', 'unshift'],
  },
  {
    title: '2ème question pour récupérer ma lettre de motivation !',
    question: 'Quel est le nom du dieu grec du vin et de la fête ?',
    inputsValues: ['Zeus', 'Dionysos', 'Eros', 'Poseidon'],
  },
  {
    title: '3ème question pour récupérer ma lettre de recommandation !',
    question:
      'Quelle directive permet de faire du rendu conditionnel avec VueJS ?',
    inputsValues: ['v-bind', 'v-for', 'v-text', 'v-if'],
  },
  {
    title: '4ème et dernière question ! Pour récupérer mes disponibilités !',
    question: 'Le Saint-Julien est un vin de ... ?',
    inputsValues: ['Loire', 'Bourgogne', 'Bordeaux', 'Franche-comté'],
  },
])
</script>

<template>
  <p>
    {{ displayData[dsplInfo.arrayIndex].title }}
  </p>
  <p>
    {{ displayData[dsplInfo.arrayIndex].question }}
  </p>
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
    />
    <label :for="inputValue">{{ inputValue }}</label>
  </div>

  <h1 v-show="dsplInfo.answer">Your answer: {{ dsplInfo.answer }}</h1>

  <div class="btn-container">
    <button @click="toggle()">Valider</button>
  </div>
</template>

<style></style>
