
<template>
  <div class="container w-4/5 mx-auto mt-4">
    <h1 class="text-4xl font-bold">Ma sélection</h1>
    Vous avez selectionné {{ selection.length }}

    <div v-if="selection.length == 0">
      <p>Aucun personnage n'as été selectionné</p>
    </div>

    <div v-else>
      
  
      <div
        v-for="(character, index) in selection"
        :key="index"
        
        class="border border-black my-4 p-2"
      >
        
         <img :src="characterPic(character.pic)" alt="">
        <h3>{{ character.name }} </h3>
        <p>Rareté: {{ character.stars }}</p>

 <base-button
      text="supprimer"
      @click="deleteCharacter(character)"
     
  
    >
    </base-button>
        
      </div>

      
    </div>
    
  </div>
  
</template>





<script>
export default {
  name: "selection-list",
  props: ['selection'],
  
  methods: {
    characterPic(img) {
      return require('@/assets/img/'+img)
    }
,
 deleteCharacter(index) {
      this.selection.splice(index, 1);
    }
  }
  
}
</script>

<style>

</style>