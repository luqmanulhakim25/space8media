<template>
  <div class="whatsapp container">
    <div
      class="whatsapp__link d-flex align-center justify-center pointer"
      @click="onWhatsapp()"
    >
      <v-icon color="white" size="30">mdi-whatsapp</v-icon>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    onWhatsapp() {
      window.open('https://api.whatsapp.com/send?phone=+628111515888')
    },
  },
}
</script>

<style lang="scss" scoped>
.whatsapp {
  &__link {
    position: fixed;
    width: 60px;
    height: 60px;
    bottom: 40px;
    right: 20px;
    background-color: #25d366;
    color: #fff;
    border-radius: 50px;
    text-align: center;
    font-size: 30px;
    // box-shadow: 2px 2px 3px #999;
    z-index: 100;
  }
}

.my-float {
  margin-top: 16px;
}
</style>
