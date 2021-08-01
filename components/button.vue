<template>
  <div>
    <b-row>
      <b-button-group @click="sendvalue">
        <router-link :to="{ name: 'errors-slug', params: { slug: 404 } }"
          ><b-button value="404">404</b-button></router-link
        >
        <router-link :to="{ name: 'errors-slug', params: { slug: 403 } }"
          ><b-button value="404">403</b-button></router-link
        >
        <router-link :to="{ name: 'errors-slug', params: { slug: 500 } }"
          ><b-button value="404">500</b-button></router-link
        >
        <router-link :to="{ name: 'errors-slug', params: { slug: 502 } }"
          ><b-button value="404">502</b-button></router-link
        >
        <router-link :to="{ name: 'errors-slug', params: { slug: 301 } }"
          ><b-button value="404">301</b-button></router-link
        >
      </b-button-group>
    </b-row>
  </div>
</template>
<script>
export default {
  methods: {
    sendvalue(e) {
      console.log(e.target?.value)
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
