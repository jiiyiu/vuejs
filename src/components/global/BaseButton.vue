<template>
  <button class="text-white font-bold py-2 px-20 rounded bg-indigo-500 hover:bg-blue-700"
  :class="{'afterclick': isClicked, 'beforeclick':!isClicked}"
  :disabled="IsDisabled">
    
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "base-button",
  props: ['text', 'IsDisabled']
}
</script>