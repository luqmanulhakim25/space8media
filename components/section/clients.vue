<template>
  <div class="clients__section">
    <v-container class="pa-0 px-4" grid-list-lg>
      <h2 class="text-center h2--xlarge primary--text text--lighten-1 mb-8">
        Trusted by Over100k+ Client
      </h2>
      <v-row align="center" justify="space-around" no-gutters>
        <v-col cols="auto" v-for="(item, i) in items" :key="i">
          <div class="mx-auto d-flex align-center justify-center">
            <v-img :width="isMobile" :src="item" alt="logo" />
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { ITEMS } from '@/data/clients'
export default {
  data: () => ({
    items: ITEMS,
  }),

  computed: {
    isMobile() {
      return this.$vuetify.breakpoint.xsOnly ? 100 : 180
    },
  },
}
</script>

<style lang="scss" scoped>
.clients__section {
  padding: 100px 0px;
}
</style>
