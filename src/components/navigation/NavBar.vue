<template>
  <div class="bg-blue-500 p-5">

    <a 
      v-for="(link, index) in navigation"
      :key="index"
      href="#" 
      @click="selectComponent(link.component)" 
    >
      {{ link.name }}
     | </a>
    
  </div>
  
</template>

<script>
export default {
  name: "nav-bar",
  data() {
    return {
      navigation: [
        { name: "Tous les joueurs", component: "character-list" },
        { name: "Ma sélection", component: "selection-list" }
      ]
    }
  },
  methods: {
    selectComponent(comp) {
      this.$emit('change-component', comp)
    }
  }
}
</script>

<style>

</style>