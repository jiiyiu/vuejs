<template>
  <div>Vous avez selectionné {{ selection.length }}
    <span v-if="nbrCharacters">Personnages</span>
    <span v-else>personnages</span>
  </div>
</template>

<script>
export default {
  name: "selection-box",
  props: ['selection'],
  computed: {
    nbrJoueurs() {
      if(this.selection.length > 1){
        return true
      }
      return false
    }
  }
}
</script>

<style>

</style>