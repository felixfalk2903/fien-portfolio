<template>
  <div class="hello">
    <pdf src="../assets/StudentAtWork-Attest-Felix-Falk.pdf"></pdf>
  </div>
</template>

<script>
import pdf from 'vue-pdf'
export default {
  name: 'FienPortfolio',
  components: {
    pdf
  },
  props: {
    path: String
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
