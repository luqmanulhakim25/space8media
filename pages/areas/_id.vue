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

    <v-card flat color="transparent" height="200" width="100%" />

    <!-- <v-container>
      <v-row align="center" justify="center">
        <v-col cols="12" md="8">
          <v-card
            class="areas__detail__card rounded-xl pa-12 d-flex flex-column justify-center align-center mt-8 mb-4"
          >
            <icon
              color="primary lighten-2"
              iconColor="white"
              icon="mdi-map-marker-outline"
              class="mb-4"
            />

            <h4 class="h4--default primary--text text-center">
              {{ item.label }}
            </h4>
            <p class="text--default primary--text mt-2 text-center">
              {{ item.address }}
            </p>
          </v-card>
        </v-col>
      </v-row>
    </v-container> -->

    <v-img class="areas__detail__header full-width" />
    <v-container class="mt-16 px-6 px-md-0">
      <v-row>
        <v-col cols="12" md="7">
          <v-img :src="item.image" class="rounded-xl elevation-2 full-height" />
        </v-col>
        <v-col cols="12" md="5">
          <v-card flat class="rounded-xl">
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
          <div class="hidden-md-and-up">
            <div
              class="d-flex flex-column justify-center align-center mt-8 mb-4"
            >
              <icon
                color="primary lighten-2"
                iconColor="white"
                icon="mdi-map-marker-outline"
                class="mb-4"
              />

              <div class="ml-4">
                <h4 class="h4--default primary--text text-center">
                  {{ item.label }}
                </h4>
                <p class="text--default primary--text mt-2 text-center">
                  {{ item.address }}
                </p>
              </div>
            </div>
          </div>
          <div class="hidden-sm-and-down">
            <div class="d-flex align-start mt-4">
              <icon
                color="primary lighten-2"
                iconColor="white"
                icon="mdi-map-marker-outline"
                size="32"
              />

              <div class="ml-4">
                <h4 class="h4--default primary--text">
                  {{ item.label }}
                </h4>
                <p class="text--default primary--text mt-2">
                  {{ item.address }}
                </p>
              </div>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
    <v-container class="py-md-16">
      <v-row>
        <v-col
          cols="6"
          md="4"
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

    <v-responsive>
      <areas />
    </v-responsive>

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
.areas__detail {
  &__header {
    background: url('https://a.cdn-hotels.com/gdcs/production2/d1963/0f6d0b5b-499c-4d1c-8995-1d2ea4f9a9a4.jpg?impolicy=fcrop&w=800&h=533&q=medium');
    background-size: cover;
    background-position-y: -150px;
    background-repeat: no-repeat;
    background-attachment: fixed;
    position: absolute;
    top: 0;
    height: 500px;
    &:before {
      content: '';
      width: 100%;
      background-color: rgba(15, 15, 43, 0.37);
      position: absolute;
      height: 100vh;
      @media (max-width: 960px) {
        height: 100vh;
      }
    }
  }

  &__card {
    z-index: 2;
    background-color: rgba(255, 255, 255, 0.7) !important;
  }
}
</style>
