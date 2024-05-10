<template>
  <main>
    <div class="mx-auto max-w-7xl py-6 sm:px-6 lg:px-8">
    <div class="results mt-3">
      <div class="flex justify-normal flex-wrap">
        <div class="cursor-pointer hover:bg-gray-700 p-2 rounded text-xl antialiased" v-for="emoji in emojis" :key="emoji.index" @click="copyToClipboard(emoji.emoji)">
          {{ emoji.emoji }}
        </div>

      </div>
    </div>
    </div>
    </main>
  </template>
  
  <script>
  export default {
    props: {
      emojis: Array
    },
    methods: {
      copyToClipboard(emoji) {
        if (navigator.clipboard) {
            navigator.clipboard.writeText(emoji).then(() => {
                alert('Emoji copied to clipboard!');
            }).catch(err => {
                console.error('Failed to copy:', err);
            });
        } else {
            console.log('Clipboard API not available');
        }
      }
    }
  }
  </script>
  