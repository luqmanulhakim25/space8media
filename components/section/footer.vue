<template>
  <div class="footer__section primary darken-2 px-16">
    <div class="d-sm-flex align-center justify-space-between">
      <div>
        <v-img
          contain
          width="200"
          src="/nav-logo-white.png"
          class="mx-auto mx-sm-0"
        />
      </div>

      <div
        class="d-md-flex justify-space-between mt-6 mt-sm-0 text-center text-sm-left"
      >
        <div class="mr-md-16">
          <p class="text--default primary--text text--lighten-1">
            Jl. Nusantara Raya No. 282, RT 11, RW 03 <br />
            Depok Jaya , Pancoran Mas <br />
            Kota Depok - Jawa Barat 16432
          </p>
        </div>
        <div class="mt-sm-4 mt-4 mt-md-0">
          <p class="text--default primary--text text--lighten-1">
            (021) 225 48589
          </p>
          <p class="text--default primary--text text--lighten-1">
            email@spacemedia.com
          </p>
        </div>
      </div>
    </div>

    <v-divider class="mt-6 mb-8 primary lighten-1"></v-divider>
    <div class="d-flex align-center flex-column">
      <p class="text--large primary--text text--lighten-1 text-center">
        Copyright © 2022 Space8MEDIA, All rights reserved
      </p>
      <v-icon
        size="36"
        color="primary lighten-1"
        class="mt-6 pointer"
        @click="onInstagram()"
        >mdi-instagram</v-icon
      >
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    onInstagram() {
      let url = 'https://instagram.com/space8media'
      window.open(url)
    },
  },
}
</script>

<style lang="scss" scoped>
.footer__section {
  padding: 80px 0px 60px 0px;
}
</style>
