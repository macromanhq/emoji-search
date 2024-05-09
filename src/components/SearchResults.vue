<template>
    <div>
      <ul>
        <li v-for="emoji in emojis" :key="emoji.index" @click="copyToClipboard(emoji.emoji)">
          {{ emoji.emoji }} - {{ emoji.name }}
        </li>
      </ul>
    </div>
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
  