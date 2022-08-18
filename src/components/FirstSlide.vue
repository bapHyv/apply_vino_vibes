<script setup>

const props = defineProps({
    toggle: {type: Function, required: true}
})

</script>

<template>
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
</template>

<style></style>
