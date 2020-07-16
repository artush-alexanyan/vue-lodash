<template>
  <div class="home">
    <div class="container">
      <div class="h4 text-center text-info">Search bar using vue lodash</div>
      <div class="container mt-1">
        <div class="input-group mb-3">
          <div class="input-group-prepend">
            <button type="button" class="btn btn-secondary"><i class="fas fa-search"></i></button>
          </div>
          <input
              placeholder="Search for items..." 
              type="text" 
              class="form-control" 
              aria-label="Text input with segmented dropdown button" 
              v-model="searchText"
              >
        </div>
        <p class="mt-3" v-if="noResult < 20 && noResult > 0"> <b> {{ noResult }} </b>  search results</p>
        <p class="text-danger mt-3" v-if="noResult == 0">No search results by : {{ searchText }} </p>
        <p><b> {{ typing }} </b> </p>
      </div>
    </div>
    <div class="container mt-3">
      <ul class="list-group">
        <li 
          class="list-group-item list-group-item-secondary mt-1"
          v-for="item in filterItems"
          :key="item.id"
          >
          <b class="mt-3">{{ item.id }}.</b>
          {{ item.title  }}
          </li>
      </ul>      
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data: () => {
    return {
      items: [],
      filters: ['completed'],
      searchText: '',
      typing: '',
      // debouncedGetAnswer: null
    }
  },
  mounted() {
    this.getQuotes()
  },
  methods: {
    getQuotes () {
    fetch('https://jsonplaceholder.typicode.com/todos/?_limit=20')
        .then(response => response.json())
        .then(json => {
            this.items = json
        })
     }
  },
  watch: {
    searchText() {
      // this.typing = 'Go ahead...'
      this.debouncedGetAnswer()
    }
  },
  created() {
    this.debouncedGetAnswer = this._.debounce(this.getQuotes, 500)
  },  
  computed: {
    filterItems() {
      return this.items.filter(item => {
          return this._.includes(item.title.toLowerCase(), this.searchText.toLowerCase())
      })
    },
    noResult() {
      return this.filterItems.length
    }
  }
}
</script>

<style scoped>
@import url('https://use.fontawesome.com/releases/v5.5.0/css/all.css');
</style>