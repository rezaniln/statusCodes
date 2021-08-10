<template>
  <div id="mainContainer" class="b1">
    <div>
      <b-row class="m-0">
        <b-col cols="9" class="h1container">
          <h1 class="zoomInUp">{{error.statusCode}}</h1>
          <h4 v-if="error.statusCode==404">
            صفحه مورد نظر پیدا نشد
          </h4>
          <h4 v-else-if="error.statusCode==403">
            دسترسی غیر مجاز
          </h4>
          <h4 v-else-if="error.statusCode==500">
            خطای داخلی سرور
          </h4>
          <h4 v-else-if="error.statusCode==502">
                درگاه خراب است
          </h4>
          <h4 v-else-if="error.statusCode==301">
                صفحه منتقل شده است
          </h4>
          <b-button class="button" pill variant="primary" @click="back">بازگشت به صفحه اصلی</b-button>
        </b-col>
      </b-row>
      <div   class="mgContainer">
          <img v-if="error.statusCode==404" src="~/assets/png/404.png" alt="">
          <img v-else-if="error.statusCode==403" src="~/assets/png/301edited.png" alt="">
          <img v-else-if="error.statusCode==500" src="~/assets/png/500.png" alt="">
          <img v-else-if="error.statusCode==502" src="~/assets/png/502edited.png" alt="">
          <img v-else-if="error.statusCode==301" src="~/assets/png/403new.png" alt="">
        </div>
    </div>
  </div>
</template>

<script>

export default {
  layout: 'empty',
 
  props: {
    error: {
      type: Object,
      default: null,
      required:true
    }
  },
  data () {
    return {
      
      statusCode: this.error.statusCode,
      test: '',
      img: null,
    }
  },
  methods: {
    back() {
    location.reload()
  }
  },
 
}
</script>

<style lang="scss" scoped>
img {
  transform: scaleX(-1);
  
  margin-left: 50px;
  float: left;
  filter: hue-rotate(162deg);
}
.rowGroup {
  flex-direction: row !important;
}
.b1 {
  margin: 0;
  position: relative;
  z-index: 1;
  overflow: hidden;
  background: linear-gradient(
    to top right,
    #ffffff 40%,
    rgb(255, 255, 255) 100%
  );
  &:before {
    width: 100% !important;
    content: '';
    top: -400px;
    left: 0;
    right: 0;
    bottom: 0;
    background-image: url(~assets/png/shapenew.png);
    filter: hue-rotate(15deg);
    background-repeat: no-repeat;
    background-position: center;
    z-index: -1;
    position: fixed;
  }
}
.row {
  width: 100%;
  flex-direction: row-reverse;
  justify-content: center;
  align-items: center;
  padding-top: 300px;
  .img-container {
    width: fit-content;
  }
}
h1 {
  text-align: center;
  font-size: 300px;
  color: #415dc2a8;
  text-shadow: 1px 3px 0 #040947, 8px 25px 10px #000000cb;
  animation-name: anime;
}
h4 {
  text-align: center;
  padding-top: 20px;
  font-size: 50px;
  color: #463e3e;
  text-shadow: 1px 2px 0 #6e6767, 1px 2px 5px #cfccca;
  color: #0000009a;
}
#cardWrap {
  display: flex;
  justify-content: center;
  align-items: center;
  transform-origin: center;
}

.zoomInUp {
  -webkit-animation-name: zoomInUp;
  animation-name: zoomInUp;
  -webkit-animation-duration: 1s;
  animation-duration: 1s;
  -webkit-animation-fill-mode: both;
  animation-fill-mode: both;
}
@-webkit-keyframes zoomInUp {
  0% {
    opacity: 0;
    -webkit-transform: scale3d(0.1, 0.1, 0.1) translate3d(0, 1000px, 0);
    transform: scale3d(0.1, 0.1, 0.1) translate3d(0, 1000px, 0);
    -webkit-animation-timing-function: cubic-bezier(0.55, 0.055, 0.675, 0.19);
    animation-timing-function: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  }
  60% {
    opacity: 1;
    -webkit-transform: scale3d(0.475, 0.475, 0.475) translate3d(0, -60px, 0);
    transform: scale3d(0.475, 0.475, 0.475) translate3d(0, -60px, 0);
    -webkit-animation-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1);
    animation-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1);
  }
}
@keyframes zoomInUp {
  0% {
    opacity: 0;
    -webkit-transform: scale3d(0.1, 0.1, 0.1) translate3d(0, 1000px, 0);
    transform: scale3d(0.1, 0.1, 0.1) translate3d(0, 1000px, 0);
    -webkit-animation-timing-function: cubic-bezier(0.55, 0.055, 0.675, 0.19);
    animation-timing-function: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  }
  60% {
    opacity: 1;
    -webkit-transform: scale3d(0.475, 0.475, 0.475) translate3d(0, -60px, 0);
    transform: scale3d(0.475, 0.475, 0.475) translate3d(0, -60px, 0);
    -webkit-animation-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1);
    animation-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1);
  }
}
.mgContainer{
position: fixed;
bottom: 0;
left:0;
z-index: 5;
}
.h1container{
  display: flex;
  flex-direction: column;
  padding-left: 700px;
  align-items: center;
  justify-content: center;
}
.button{
  margin-top: 30px;
  padding:15px 70px;
}
</style>