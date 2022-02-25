<template>
  <div class="clients__section" v-scroll-spy>
    <v-container class="pa-0 hidden-sm-and-down" grid-list-lg>
      <h2 class="text-center h2--xlarge primary--text text--lighten-1 mb-16">
        Trusted by Over100k+ Client
      </h2>
      <v-row align="center" justify="space-between" no-gutters>
        <v-col cols="12" md="2" v-for="(item, i) in items" :key="i">
          <div class="mx-auto d-flex align-center justify-center">
            <img :src="item" alt="logo" />
          </div>
        </v-col>
      </v-row>
    </v-container>

    <mobile-clients class="hidden-sm-and-up" :items="items" />
  </div>
</template>

<script>
import { ITEMS } from '@/data/clients'
export default {
  data: () => ({
    items: ITEMS,
  }),
}
</script>

<style lang="scss" scoped>
.clients__section {
  padding: 100px 0px;
}
</style>
