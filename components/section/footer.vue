<template>
  <div class="footer__section primary darken-2 px-16">
    <div class="d-md-flex align-center justify-space-between">
      <div>
        <v-img contain width="200" src="/nav-logo-white.png" />
      </div>

      <div class="d-md-flex justify-space-between">
        <div class="primary--text text--lighten-1 text--large mr-16">
          <p>Jl. Lorem ipsum</p>
          <p>Cilandak, Jakarta Selatan</p>
          <p>Indonesia, 14045</p>
        </div>
        <div class="primary--text text--lighten-1 text--large">
          <p>(021) 225 48589</p>
          <p>email@spacemedia.com</p>
        </div>
      </div>
    </div>
    <div class="mt-6 ml-2">
      <v-icon size="36" color="primary lighten-1" class="mr-2"
        >mdi-facebook</v-icon
      >
      <v-icon size="36" color="primary lighten-1" class="mr-2"
        >mdi-instagram</v-icon
      >
      <v-icon size="36" color="primary lighten-1">mdi-twitter</v-icon>
    </div>

    <v-divider class="mt-6 mb-8 primary lighten-1"></v-divider>
    <div class="d-md-flex align-center justify-space-between">
      <div>
        <p class="text--large primary--text text--lighten-1">
          Copyright © 2022 Space8MEDIA, All rights reserved
        </p>
      </div>

      <div class="hidden-sm-and-down">
        <span
          class="px-6 primary--text text--lighten-1"
          v-for="(item, index) in items.menu"
          :key="index"
          >{{ item.label }}</span
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    items: {
      menu: [
        { id: 1, label: 'Home' },
        { id: 1, label: 'Areas' },
        { id: 1, label: 'Products' },
        { id: 1, label: 'Contact Us' },
      ],
    },
  }),
}
</script>

<style lang="scss" scoped>
.footer__section {
  padding: 80px 0px 60px 0px;
}
</style>
