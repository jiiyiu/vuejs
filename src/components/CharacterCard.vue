<template>
  
  <div 
    class="box-content border-green-900 m-8 p-10 border-1 rounded flex justify-between"
   
    :class="CanDropClass"
  >
    <div>
      <ul>
       <img :src="characterPic(character.pic)" alt="">
      </ul>
      <ul>
      <h3 class="font-serif text-lg text-gray-800">{{ characterName }} | {{ character.stars }}</h3>
        <li class="text-sm">Origines: {{character.country}} </li>
        <li class="text-sm"> Arme utilisé: {{character.wearpon}}</li>
      </ul>
      <p class="font-serif text-lg text-gray-800 italic tracking-wide">"{{ character.quote }}"</p>
    </div>
    
 <div v-if="this.character.drop === 'available'" >
    <base-button
      text="Sélectionner"
      @click="addToSelection"
     
  
    >
    </base-button>
    
    
</div>
    <div v-else-if="this.character.drop === 'out'">

    </div>


  </div>
</template>

<script>
export default {
  name: "character-card",
  props: ['character', 'character-index'],
  data(){
    return{
  
    }
  },
  computed: {
   characterName() {
      if(this.character.name.split('.').length > 1){
        return this.character.name.split('.')[1]
      }
      return this.character.name;
    },
    characterDrop() {
      if(this.character.drop == "out"){
        return true
      }
      return false
    },
    CanDropClass() {
      return { 
        '': this.characterDrop, 
        'bg-green-200': !this.characterDrop
        }
    },
  },
  methods: {
    characterPic(img) {
      return require('@/assets/img/'+img)
    },
    addToSelection() {
      this.$emit('add-character', this.character)
    }
    
  }
}
</script>
