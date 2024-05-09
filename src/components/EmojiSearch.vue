<template>
    <div>
      <input type="text" @input="onInput" placeholder="Type to search emojis...">
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      onInput(event) {
        this.$emit('search', event.target.value);
      }
    }
  }
  </script>
  