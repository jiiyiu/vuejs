<template>
  <nav-bar
    @change-component="updateSelectedComponent"
  ></nav-bar>


  <keep-alive>
    <component 
      :is="selectedComponent"
      v-bind="currentProps"
      @update-selection="updateSelection"
      @delete-selection="deleteSelection"
    >
    </component>
  </keep-alive>
  
 
</template>

<script>
import CharacterList from './components/CharacterList.vue'
import SelectionList from './components/SelectionList.vue'

import NavBar from './components/navigation/NavBar.vue'

export default {
  name: 'App',
  components: {
    CharacterList,
    NavBar,
    SelectionList
  },
  data() {
    return {
      selectedComponent: 'character-list',
      selectionArray: []
    }
  },
  computed: {
    currentProps() {
      if(this.selectedComponent == "selection-list") {
        return { selection: this.selectionArray }
      }
      return false
    }
  },
  methods: {
    updateSelectedComponent(comp) {
      this.selectedComponent = comp
    },
    updateSelection(character) {
      this.selectionArray.push(character)
    },
    deleteSelection(index){
      this.selectionArray.splice(index, 1)
    }
    }
  }

</script>
<style>

</style>
