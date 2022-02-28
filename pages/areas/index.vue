<template>
  <div class="areas d-flex flex-column align-center">
    <v-card flat color="primary" height="82" width="100%"></v-card>
    <!-- <v-img class="areas__header full-width" height="300" src="/hero.jpg" /> -->

    <v-container class="py-md-16">
      <v-row>
        <v-responsive class="container mb-n6">
          <p class="h5--small primary--text mb-4">Find Your Location</p>
          <vs-input v-model="search" block placeholder="Find location">
            <template #icon>
              <v-icon>mdi-magnify</v-icon>
            </template>
          </vs-input>
        </v-responsive>
        <v-col
          cols="6"
          md="3"
          v-for="(item, index) in isFilterAreas"
          :key="index"
          class="mt-6"
        >
          <v-card flat class="areas__card pointer" @click="onDetail(item)">
            <v-img height="180" :src="item.image" class="rounded" />
            <div class="white px-4">
              <p class="areas__label h6--xsmall primary--text">
                {{ item.label }}
              </p>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { AREAS } from '@/data/areas'
export default {
  data: () => ({
    search: '',
    areas: AREAS,
  }),

  computed: {
    isFilterAreas() {
      const insensitive = new RegExp(this.search?.replace(/\\/g, '\\\\'), 'i')
      return this.areas.filter((item) => {
        return item.label.match(insensitive)
      })
    },
  },

  methods: {
    onDetail(item) {
      this.$router.push(`/areas/${item.slug}`)
    },
  },

  watch: {
    $route: {
      handler(val) {
        this.search = val.hash ? val.hash.replace('#', '') : ''
      },
      immediate: true,
    },
  },
}
</script>

<style lang="scss" scoped>
.areas {
  &__label {
    background-color: white;
    padding: 0px 16px;
    position: absolute;
    bottom: 10px;
  }

  &__card {
    transition: all 0.25s ease;
    box-shadow: 0px 5px 20px 0px rgba(0, 0, 0, var(--vs-shadow-opacity)) !important;
    &:hover {
      transform: translate(0, -5px);
      box-shadow: 0px 12px 26px rgba(0, 69, 172, 0.14) !important;
    }
  }
}
</style>
