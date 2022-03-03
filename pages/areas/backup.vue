<template>
  <div class="areas d-flex flex-column align-center" v-show="item">
    <v-card flat color="primary" height="82" width="100%"></v-card>
    <!-- <v-img class="areas__header full-width" height="300" src="/hero.jpg" /> -->
    <v-container class="mt-16 px-6 px-md-0">
      <v-row>
        <v-col cols="12" md="7">
          <v-img :src="item.image" class="rounded-xl elevation-2 full-height" />
        </v-col>
        <v-col cols="12" md="5">
          <div class="d-flex flex-column align-center">
            <icon
              color="primary lighten-2"
              iconColor="white"
              class="mb-4"
              icon="mdi-map-marker-outline"
            />
            <h4 class="h4--default primary--text">{{ item.label }}</h4>
            <p class="text--default parimary--text mb-6 mt-1">
              {{ item.address }}
            </p>
          </div>
          <v-card flat>
            <div class="primary lighten-2 py-2 px-4">
              <p class="h7--xxsmall white--text">Location</p>
            </div>
            <iframe
              :src="isLocation"
              height="295"
              class="full-width"
              style="border: 0"
              loading="lazy"
            ></iframe>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <v-container class="py-md-16">
      <v-row>
        <v-col
          cols="6"
          md="3"
          v-for="(item, index) in products"
          :key="index"
          class="mt-6"
        >
          <div class="d-flex flex-column align-center">
            <v-icon size="26" color="primary lighten-2">{{ item.icon }}</v-icon>
            <p class="h7--xxsmall accent--text">
              {{ item.label }}
            </p>
            <p class="text--default dark--text text-center">
              {{ item.description }}
            </p>
          </div>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <vs-button class="mx-auto h7--xxsmall mt-12" @click="onOpen()"
            >More Information</vs-button
          >
        </v-col>
      </v-row>
    </v-container>
    <div class="hidden-xs-only">
      <section-areas />
    </div>

    <dialog-information :dialog="state.isDialog" @on:close="onClose" />
  </div>
</template>

<script>
import { AREAS } from '@/data/areas'
export default {
  data: () => ({
    item: {},
    areas: AREAS,
    products: [
      {
        id: 1,
        icon: 'mdi-bulletin-board',
        label: 'Media Type',
        description: 'Billboard, Frontlight, Horizontal',
      },
      {
        id: 2,
        icon: 'mdi-view-dashboard-outline',
        label: 'Total Unit',
        description: '1 Side',
      },
      {
        id: 3,
        icon: 'mdi-eye',
        label: 'Traffic viewers per day',
        description: '90.910',
      },
      {
        id: 4,
        icon: 'mdi-arrange-send-backward',
        label: 'Media Size',
        description: '5 x 10 Meter',
      },
      {
        id: 5,
        icon: 'mdi-binoculars',

        label: 'View From',
        description: 'Margonda Depok 2',
      },
      {
        id: 6,
        icon: 'mdi-map-marker-outline',
        label: 'Coordinate',
        description: '-6.938310, 109.31930',
      },
      {
        id: 7,
        icon: 'mdi-magnify',
        label: 'Point of Interest',
        description: 'Hotel, Minimarket, Universitas, Resto, Mall, Apartment',
      },
      {
        id: 7,
        icon: 'mdi-magnify',
        label: 'Point of Interest',
        description: 'Hotel, Minimarket, Universitas, Resto, Mall, Apartment',
      },
    ],
    state: {
      isDialog: false,
    },
  }),

  mounted() {
    let slug = this.$route.params.id
    let areaDetail = this.areas.find((item) => {
      return item.slug === slug
    })

    this.item = areaDetail
  },

  computed: {
    isLocation() {
      let location = this.item.address

      return `https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3965.1139019296297!2d106.82881081529514!3d-6.379295695383953!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e69ec11e6ecbe35%3A0x45e4fdba5c9fa9c0!2s${location}!5e0!3m2!1sen!2sid!4v1646018618417!5m2!1sen!2sid`
    },
  },

  methods: {
    onOpen() {
      this.state.isDialog = true
    },

    onClose() {
      this.state.isDialog = false
    },
  },
}
</script>

<style lang="scss" scoped>
.areas {
  &__header {
    &:before {
      content: '';
      width: 100%;
      height: 100%;
      background-color: rgba(2, 2, 39, 0.082);
      position: absolute;
    }
  }
}
</style>
