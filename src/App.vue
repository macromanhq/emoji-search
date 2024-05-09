<template>
  <div id="app">
    <EmojiSearch @search="handleSearch" />
    <SearchResults :emojis="filteredEmojis" />
  </div>
</template>

<script>
import EmojiSearch from './components/EmojiSearch.vue';
import SearchResults from './components/SearchResults.vue';

export default {
  name: 'App',
  components: {
    EmojiSearch,
    SearchResults
  },
  data() {
    return {
      emojis: [], // This will store all emojis
      filteredEmojis: [] // This will store emojis to display
    };
  },
  methods: {
    handleSearch(query) {
      if (query) {
        this.filteredEmojis = this.emojis.filter(emoji =>
          emoji.name.toLowerCase().includes(query.toLowerCase())
        );
      } else {
        this.filteredEmojis = this.emojis.slice(0, 10); // Reset to default view
      }
    }
  },
  created() {
    fetch('./emojis.json') // Assuming emojis.json is in the assets directory
      .then(response => response.json())
      .then(data => {
        this.emojis = data;
        this.filteredEmojis = data.slice(0, 10); // Load default emojis on creation
      });
  }
}
</script>
