<template>
  <main>
    <div class="mx-auto max-w-7xl py-6 sm:px-6 lg:px-8">
      <div class="results mt-3">
        <div class="flex justify-normal flex-wrap">
          <div class="cursor-pointer hover:bg-gray-700 p-2 rounded text-xl antialiased" v-for="emoji in emojis"
            :key="emoji.index" @click="copyToClipboard(emoji.emoji)">
            {{ emoji.emoji }}
          </div>
          <NotificationComponent ref="notification" message="Emoji has been copied to clipboard!" :emoji="lastCopiedEmoji" />

        </div>
      </div>
    </div>
  </main>
</template>

<script>
import NotificationComponent from './NotificationComponent.vue';

export default {
  components: {
    NotificationComponent
  },
  props: {
    emojis: Array
  },
  data() {
    return {
      lastCopiedEmoji: ''
    };
  },
  methods: {
    copyToClipboard(emoji) { 
      if(navigator.clipboard){
        navigator.clipboard.writeText(emoji).then(() => {
        this.lastCopiedEmoji = emoji; 
      }, (err) => {
        console.error('Failed to copy:', err);
      });

      } else {
        alert('You may have javascript disabled or on localhost');
      }
      
    }
  }
}
</script>