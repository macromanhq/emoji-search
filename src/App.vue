<template>
  <div id="app">
    <NavBar />
    <EmojiSearch @search="handleSearch" />
    
    <SearchResults :emojis="filteredEmojis" />
    <FooterBar />
  </div>
</template>

<script>
import EmojiSearch from './components/EmojiSearch.vue';
import SearchResults from './components/SearchResults.vue';
import NavBar from './components/NavBar.vue';
import FooterBar from './components/FooterBar.vue';

export default {
  name: 'App',
  components: {
    EmojiSearch,
    SearchResults,
    NavBar,
    FooterBar,
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
        this.filteredEmojis = this.emojis.slice(0, 50); // Reset to default view
      }
    }
  },
  created() {
    fetch('./emojis.json') 
      .then(response => response.json())
      .then(data => {
        this.emojis = data;
        this.filteredEmojis = data.slice(0, 50); 
      });
  }
}
</script>
