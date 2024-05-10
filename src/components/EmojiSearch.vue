<template>
  <header class="bg-white shadow">
    <div class="mx-auto max-w-7xl px-4 py-6 sm:px-6 lg:px-8">
      <input type="text" @input="onInput" placeholder="Type to search emojis..." class="mt-1 block w-full px-3 py-2 bg-white border border-gray-300 rounded-md text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm">
    </div>
  </header>
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
  