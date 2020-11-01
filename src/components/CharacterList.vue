<template>
<h1 text-4xl>Liste des personnages de {{charactersData.name}}</h1>



 <selection-box 
    :selection="selection"
  >
  </selection-box>

<character-card
v-for="(character, index) in charactersData.characters"
:key="index"
:character="character"

@add-character="addCharacterToSelection"

>
</character-card>
</template>

<script>
import charactersData from '../assets/data/characters.json'
import CharacterCard from './CharacterCard.vue'
import SelectionBox from './SelectionBox.vue'

export default{
    name:"character-List",
  components: {
      CharacterCard,
       SelectionBox,
  },
  data(){
      return{
          charactersData:charactersData,
          selection:[],
    
      }
  },
  methods:{
      addCharacterToSelection(character){
          this.selection.push(character)
          this.$emit('update-selection', character)

      }

  }
}
</script>
<style>

</style>