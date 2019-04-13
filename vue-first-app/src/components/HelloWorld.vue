<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="toogleFilter"> {{ filtrActive ? 'disable filtr' : 'enable filtr' }} </button>
    <ul>
      <li v-for="element in filteredTab" v-bind:key="element">
        {{ element }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      tab: [1,2,3,4,5,6,7,8,9,10],
      filter: 5,
      filterActive: false,
    }
  },
  methods: {
    toogleFilter() {
      this.filterActive = !this.filterActive;
    },
  },
  computed: {
    filteredTab: function() {
      return this.tab.filter((x) => {
        const currentFiltr = this.filterActive ? this.filter : 0;
        return x > currentFiltr;
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
