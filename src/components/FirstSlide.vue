<script setup>
const props = defineProps({
  toggle: { type: Function, required: true },
})
</script>

<template>
    <p class="first-p">Vous chercher à recruter un développeur web?</p>
    <p class="second-p">
      Commencez ce quiz de 4 questions pour obtenir mes informations !
    </p>

    <div class="btn-container">
      <button @click="toggle()">Commencer</button>
      <button class="btn-cancel">Annuler</button>
    </div>
    <p class="third-p">
      Si vous ne souhaitez pas jouer au jeu, appuyez sur annuler pour
      télécharger un dossier zip qui contient mon cv, ma lettre de motivation,
      une lettre de recommandation et mes disponibilites
    </p>
</template>

<style>
</style>
