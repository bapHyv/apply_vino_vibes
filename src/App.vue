<script setup>
import { ref } from 'vue'

const show = ref(true)
const cardNb = ref(1)
const answer = ref('')

const validate = () => {
  show.value = !show.value
  cardNb.value++
  answer.value = ''
}

const toggle = () => {
  if (cardNb.value === 1 && answer.value === '') {
    show.value = !show.value
    cardNb.value++
  }
  if (cardNb.value === 2 && answer.value === 'pop') {
    validate()
  }
  if (cardNb.value === 3 && answer.value === 'Dionysos') {
    validate()
  }
  if (cardNb.value === 4 && answer.value === 'v-if') {
    validate()
  }
  if (cardNb.value === 5 && answer.value === 'Bordeaux') {
    validate()
  }
}
</script>

<template>
  <Transition name="slide">
    <section v-if="show && cardNb === 1" class="content-container">
      <p>Vous chercher à recruter un développeur web?</p>
      <p>Commencez ce quiz de 4 questions pour obtenir mes informations !</p>
      <p>
        Si vous ne souhaitez pas jouer le jeu, appuyez sur annuler pour
        télécharger un dossier zip qui contient mon CV, ma lettre de motivation,
        une lettre de recommandation et mes disponibilités
      </p>
      <div class="btn-container">
        <button @click="toggle()">Commencer</button>
        <button>Annuler</button>
      </div>
    </section>
  </Transition>

  <Transition name="slide">
    <section v-if="!show && cardNb === 2" class="content-container">
      <p>SUPER !! Vous avez donc envie de faire ce quiz !</p>
      <p>1ère question pour récupérer mon CV!</p>
      <p>
        Quelle est la méthode JS qui supprime le dernier élément d'un tableau et
        le renvoie?
      </p>
      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="push"
          id="push"
          value="push"
        />
        <label for="push">push()</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="shift"
          id="shift"
          value="shift"
        />
        <label for="shift">shift()</label>
      </div>

      <div class="input-and-label-container">
        <input type="radio" v-model="answer" name="pop" id="pop" value="pop" />
        <label for="pop">pop()</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="unshift"
          id="unshift"
          value="unshift"
        />
        <label for="unshift">unshift()</label>
      </div>

      <h1 v-show="answer">Your answer: {{ answer }}</h1>

      <div class="btn-container">
        <button @click="toggle()">Valider</button>
      </div>
    </section>
  </Transition>

  <Transition name="slide">
    <section v-if="show && cardNb === 3" class="content-container">
      <p>
        2ème question pour récupérer ma lettre de motivation !
      </p>
      <p>
        Quel est le nom du dieu grec du vin et de la fête?
      </p>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="Zeus"
          id="Zeus"
          value="Zeus"
        />
        <label for="Zeus">Zeus</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="Dionysos"
          id="Dionysos"
          value="Dionysos"
        />
        <label for="Dionysos">Dionysos</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="Eros"
          id="Eros"
          value="Eros"
        />
        <label for="Eros">Eros</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="v-if"
          id="Poseidon"
          value="Poseidon"
        />
        <label for="Poseidon">Poséidon</label>
      </div>

      <h1 v-show="answer">Your answer: {{ answer }}</h1>

      <div class="btn-container">
        <button @click="toggle()">Valider</button>
      </div>
    </section>
  </Transition>

  <Transition name="slide">
    <section v-if="!show && cardNb === 4" class="content-container">
      <p>
        3ème question pour récupérer ma lettre de recommandation !
      </p>
      <p>Quelle directive permet de faire du rendu conditionnel avec VueJS?</p>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="v-bind"
          id="v-bind"
          value="v-bind"
        />
        <label for="v-bind">v-bind</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="v-for"
          id="v-for"
          value="v-for"
        />
        <label for="v-for">v-for</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="v-text"
          id="v-text"
          value="v-text"
        />
        <label for="v-text">v-text</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="v-if"
          id="v-if"
          value="v-if"
        />
        <label for="v-if">v-if</label>
      </div>

      <h1 v-show="answer">Your answer: {{ answer }}</h1>

      <div class="btn-container">
        <button @click="toggle()">Valider</button>
      </div>
    </section>
  </Transition>

  <Transition name="slide">
    <section v-if="show && cardNb === 5" class="content-container">
      <p>
        4ème et dernière question ! Pour récupérer mes disponibilités !
      </p>
      <p>Le Saint-Julien est un vin de ...?</p>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="Loire"
          id="Loire"
          value="Loire"
        />
        <label for="Loire">Loire</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="Bourgogne"
          id="Bourgogne"
          value="Bourgogne"
        />
        <label for="Bourgogne">Bourgogne</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="Bordeaux"
          id="Bordeaux"
          value="Bordeaux"
        />
        <label for="Bordeaux">Bordeaux</label>
      </div>

      <div class="input-and-label-container">
        <input
          type="radio"
          v-model="answer"
          name="Franche-comté"
          id="Franche-comté"
          value="Franche-comté"
        />
        <label for="Franche-comté">Franche-comté</label>
      </div>

      <h1 v-show="answer">Your answer: {{ answer }}</h1>

      <div class="btn-container">
        <button @click="toggle()">Valider</button>
      </div>
    </section>
  </Transition>

  <Transition name="slide">
    <section v-if="!show && cardNb === 6" class="content-container">
      <p>
        Bravo ! Vous êtes arrivés jusqu'au bout de ce quiz! Pas trop dur? (Ne
        répondez pas, je ne vous entend pas...)
      </p>
      <p>
        Si jamais les téléchargement n'ont pas fonctionné, vous pouvez appuyer
        sur le bouton "Télécharger les documents" (On ne sait jamais hein?)
      </p>

      <div class="btn-container">
        <button @click="console.log('ntm')">Télécharger les documents</button>
      </div>
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
