<template>
  <div class="hello">
    <!-- <img src="../assets/2.png" alt="boe"> -->
    <!-- <pdf src="/1.pdf"></pdf> -->
    <vue-pdf-embed ref="pdfRef" :source="pdfSource" :page="page" @password-requested="handlePasswordRequest"
      @rendered="handleDocumentRender" />
  </div>
</template>

<script>
import VuePdfEmbed from 'vue-pdf-embed'
export default {
  name: 'FienPortfolio',
  components: {
    VuePdfEmbed
  },
  props: {
    path: String
  },
  data() {
    return {
      isLoading: true,
      page: null,
      pageCount: 1,
      pdfSource: 'Portfolio_FienCoolman_updated.pdf',
      showAllPages: true,
    }
  },
  // watch: {
  //   showAllPages() {
  //     this.page = this.showAllPages ? null : 1
  //   },
  // },
  methods: {
    handleDocumentRender() {
      this.isLoading = false
      this.pageCount = this.$refs.pdfRef.pageCount
    },
    handlePasswordRequest(callback, retry) {
      callback(prompt(retry
        ? 'Enter password again'
        : 'Enter password'
      ))
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
  width: 100%;
}
.app-header {
  padding: 0px;
  box-shadow: 0 2px 8px 4px rgba(0, 0, 0, 0.1);
  background-color: #555;
  color: #ddd;
}

body {
  margin: 0;
  padding: 0;
  background-color: #ccc;
}
</style>
