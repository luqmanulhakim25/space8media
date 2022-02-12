<template>
  <v-lazy
    v-model="isActive"
    :options="{
      threshold: 0.5,
    }"
    min-height="200"
    transition="fade-transition"
  >
    <div class="client-logo-container">
      <v-container class="pa-0" grid-list-lg>
        <h2 class="text-center h2--xlarge primary--text text--lighten-1 mb-16">
          Trusted by Over100k+ Client
        </h2>
        <v-row align="center" justify="space-between" no-gutters>
          <v-col cols="4" md="2" v-for="(item, i) in logo" :key="i">
            <div class="mx-auto d-flex align-center justify-center">
              <img :src="item" alt="logo" />
            </div>
          </v-col>
        </v-row>
      </v-container>
    </div>
  </v-lazy>
</template>

<script>
export default {
  data: () => ({
    isActive: false,
    logo: [
      './clients/client-1.svg',
      './clients/client-2.svg',
      './clients/client-3.svg',
      './clients/client-4.svg',
      './clients/client-5.svg',
    ],
  }),
}
</script>

<style lang="scss" scoped>
.client-logo-container {
  padding: 100px 0px;
}
</style>
