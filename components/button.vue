<template>
  <div>
    <b-row>
      <b-button-group id="btnGrp" @click="sendvalue">
        <b-button value="404">404</b-button>
        <b-button value="403">403</b-button>
        <b-button value="500">500</b-button>
        <b-button value="502">502</b-button>
        <b-button value="301">301</b-button>
      </b-button-group>
    </b-row>
  </div>
</template>
<script>
export default {
  data() {
    return {
      statusCode: null,
    }
  },

  methods: {
    sendvalue(e) {
      this.statusCode = e.target.value
      this.$nuxt.error({ statusCode: `${this.statusCode}`, message: 'msg' })
    },
  },
}
</script>
<style lang="scss" scoped>
.row {
  justify-content: center;
  margin-top: 100px;
  background: red;
}
</style>
