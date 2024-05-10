<template>
    <transition name="fade">
      <div v-if="isVisible" class="fixed bottom-5 right-5 bg-gray-800 text-white px-4 py-2 rounded shadow-lg" @click="hide">
        {{ message }} {{ emoji }}
      </div>
    </transition>
  </template>
  
  <script>
  export default {
    name: 'NotificationComponent',
    props: {
      message: String,
      emoji: String,
      timeout: Number
    },
    data() {
      return {
        isVisible: false
      };
    },
    methods: {
      show() {
        this.isVisible = true;
        setTimeout(() => {
          this.isVisible = false;
        }, this.timeout || 2000); // Default to 2 seconds if no timeout is provided
      },
      hide() {
        this.isVisible = false;
      }
    },
    watch: {
      emoji(newVal, oldVal) {
        if (newVal !== oldVal) {
          this.show();
        }
      }
    }
  }
  </script>
  
  <style scoped>
  .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
    opacity: 0;
  }
  </style>
  