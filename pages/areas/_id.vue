<template>
  <div
    class="areas__detail d-flex flex-column align-center justify-center"
    v-show="item"
  >
    <v-card
      flat
      color="primary darken-3"
      height="82"
      width="100%"
      style="z-index: 1"
    />

    <v-container>
      <v-row align="center" justify="center">
        <v-col cols="12" sm="8">
          <v-card
            flat
            class="areas__detail__card rounded-xl pa-12 d-flex flex-column justify-center align-center mt-8 mb-4"
          >
            <icon
              color="primary lighten-2"
              iconColor="white"
              icon="mdi-map-marker-outline"
              class="mb-4"
            />

            <h4 class="h3--large white--text text-center text-capitalize">
              {{ item.slug }}
            </h4>
            <p class="h6--xsmall white--text mt-2 text-center">
              {{ item.address }}
            </p>
          </v-card>
        </v-col>
      </v-row>
    </v-container>

    <v-img class="areas__detail__header full-width" />
    <v-container class="px-6 px-md-0">
      <v-row>
        <v-col cols="12" sm="7">
          <v-img
            :src="item.media_image"
            class="rounded-xl elevation-5 full-height"
          />
        </v-col>
        <v-col cols="12" sm="5">
          <v-card flat class="rounded-xl" color="transparent">
            <div class="primary lighten-2 py-2 px-4">
              <p class="h6--xsmall white--text">Location</p>
            </div>

            <iframe
              :src="item.coordinate"
              height="300"
              width="100%"
              style="border: 0"
              allowfullscreen=""
              loading="lazy"
            />
          </v-card>
          <div class="hidden-sm-and-down">
            <v-container pa-0>
              <v-row>
                <v-col cols="12">
                  <vs-button
                    block
                    class="mx-auto h7--xxsmall"
                    @click="onOpen(item)"
                    >More Informations</vs-button
                  >
                  <div
                    class="d-flex align-start mt-6"
                    v-for="(item, index) in item.spesifications"
                    :key="index"
                  >
                    <v-icon size="26" color="primary lighten-2">{{
                      item.icon
                    }}</v-icon>
                    <div class="ml-4">
                      <p class="h7--xxsmall accent--text">{{ item.label }}</p>
                      <p class="text--default dark--text">
                        {{ item.description }}
                      </p>
                    </div>
                  </div>
                </v-col>
              </v-row>
            </v-container>
          </div>
        </v-col>
      </v-row>
    </v-container>

    <v-container class="py-md-16 hidden-md-and-up">
      <v-row align="center" justify="center" no-gutters>
        <v-col
          cols="12"
          md="4"
          sm="4"
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
        <v-col cols="12"> </v-col>
      </v-row>
    </v-container>

    <vs-button
      class="mx-auto h7--xxsmall my-md-16 my-6 hidden-md-and-up"
      @click="onOpen(item)"
      >More Information</vs-button
    >

    <div class="hidden-md-and-down my-md-16">
      <section-areas />
    </div>

    <v-responsive>
      <areas />
    </v-responsive>

    <dialog-information
      :dialog="state.isDialog"
      @on:close="onClose"
      :pdf="state.pdf"
    />
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
        description: 'Billboard Horizontal/Vertical, Frontlight/Backlight',
      },

      {
        id: 3,
        icon: 'mdi-eye',
        label: 'Traffic viewers per day',
        description: '90.910',
      },

      {
        id: 7,
        icon: 'mdi-magnify',
        label: 'Point of Interest',
        description: 'Hotel, Minimarket, Universitas, Resto, Mall & Apartment',
      },
    ],
    state: {
      isDialog: false,
      pdf: '',
    },
  }),

  mounted() {
    let slug = this.$route.params.id
    let areaDetail = this.areas.find((item) => {
      return item.slug === slug
    })

    this.item = areaDetail
  },

  methods: {
    onOpen(item) {
      this.state.pdf = item.pdf
      this.state.isDialog = true
    },

    onClose() {
      this.state.isDialog = false
    },
  },
}
</script>

<style lang="scss" scoped>
.areas__detail {
  &__header {
    // filter: blur(1px);
    // -webkit-filter: blur(1px);
    background: url('https://images.unsplash.com/photo-1541535650810-10d26f5c2ab3?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8NHx8dGltZXMlMjBzcXVhcmV8ZW58MHx8MHx8&w=1920&q=1080');
    background-size: cover;
    background-position-y: -250px;
    background-repeat: no-repeat;
    background-attachment: fixed;
    position: absolute;
    top: 0;
    height: 500px;
    @media (max-width: 600px) {
      height: 500px;
    }
    @media (min-width: 601px) and (max-width: 960px) {
      background-size: auto;
    }

    &:before {
      content: '';
      width: 100%;
      background-color: rgba(26, 27, 39, 0.603) !important;
      position: absolute;
      height: 100vh;
      @media (max-width: 600px) {
        height: 95%;
        background-attachment: fixed;
      }
      @media (min-width: 601px) and (max-width: 960px) {
        height: 100%;
      }
    }
  }

  &__card {
    z-index: 2;
    background-color: rgba(37, 37, 37, 0.37) !important;
  }
}
</style>
