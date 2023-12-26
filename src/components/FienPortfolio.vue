<template>
  <div class="app-header">
    <!-- <img src="../assets/2.png" alt="boe"> -->
    <!-- <pdf src="/1.pdf"></pdf> -->
    <div class="app-content">
      <vue-pdf-embed ref="pdfRef" :source="pdfSource" :page="page" @password-requested="handlePasswordRequest"
      @rendered="handleDocumentRender" />
    </div>
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
      pdfSource: 'Portfolio_FienCoolman_updated_without_p.pdf',
      showAllPages: true,
    }
  },
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
<style >
body {
  margin: 0;
  padding: 0;
  background-color: rgba(235, 235, 235, 0.986);
}

.vue-pdf-embed {
  margin: auto;

  & > div {
    margin-bottom: 15px;
  }
}


.app-content {
  padding: 15px 15px;
}

.right {
  float: right;
}

</style>
