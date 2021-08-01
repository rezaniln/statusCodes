<template>
  <div>
    <div></div>
    <div>
      <b-row class="m-0">
        <b-co class="img-container">
          <img src="~/assets/gifs/20210801_020119.gif" alt="" />
        </b-co>
        <b-co
          ><h1>{{ filterStatuscode()[0].id }}</h1></b-co
        >
        <h4>{{ filterStatuscode()[0].message }}</h4>
        <p></p>
      </b-row>
    </div>
  </div>
</template>

<script>
import statusData from '~/assets/statusCodes.json'
export default {
  data() {
    return {
      list: statusData,
      statusCode: this.$route.params.slug,
      error: '',
    }
  },
  methods: {
    filterStatuscode() {
      return this.list.filter((er) => er.id === this.statusCode)
    },
  },
}
</script>
style.backdropFilter='unset'

<style lang="scss" scoped>
.row {
  width: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .img-container {
    width: fit-content;
    z-index: -5;
  }
}
h1 {
  font-size: 100px;
  color: #463e3e;
  background: #2e2b2b;
  text-shadow: 1px 3px 0 #969696, 1px 13px 5px #aba8a8;
  color: #7e7373;
  background: #fffafa;
}
#cardWrap {
  display: flex;
  justify-content: center;
  align-items: center;
  transform-origin: center;
}
</style>
