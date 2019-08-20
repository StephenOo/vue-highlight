<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="search" @input="searchText()">
    <ul>
      <li v-for="(item,index) in results" :key="index" v-html="item"></li>
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
      search: '',
      results: ['C·Ronaldo', 'Messi', 'Ramos', 'Modric', 'Marcelo', 'Bale', 'Isco'],
      copy: ['C·Ronaldo', 'Messi', 'Ramos', 'Modric', 'Marcelo', 'Bale', 'Isco'],
      update: true
    }
  },
  methods: {
    searchText() {
      Object.assign(this.results, this.copy)
      this.results.forEach((item, index) => {
        // let replaceReg = new RegExp(this.search, 'g')
        let replaceString = '<span style="color: #3bbe64;">' + this.search + '</span>'
        let res = item.replace(this.search, replaceString)
        this.$set(this.results, index, res)
      })
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
</style>
