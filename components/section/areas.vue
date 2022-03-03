<template>
  <div
    class="areas__section justify-center align-center d-flex flex-column pb-16"
  >
    <icon
      color="primary lighten-1"
      iconColor="white"
      class="mb-4"
      icon="mdi-map-marker-outline"
    />
    <h2 class="h2--xlarge primary--text text--darken-1 text-center mb-4">
      Recommended Areas
    </h2>
    <v-responsive width="800">
      <p
        class="primary--text text--lighten-1 text--large text-center mb-10 px-4"
      >
        Our products are widely distributed and offer an advertising experience
        with various famous landmarks in Indonesia, such as Jakarta, Bandung to
        Medan. So, you can place ads anywhere
      </p>
    </v-responsive>
    <v-responsive>
      <client-only>
        <carousel v-bind="options" :perPage="isPerPage">
          <slide
            v-for="(item, index) in items"
            :key="index"
            class="areas__section__slider"
          >
            <img :src="item.image" class="pointer" @click="onDetail(item)" />
            <v-card
              flat
              class="areas__section__slider__label d-inline-block px-4"
            >
              <p class="h7--xxsmall primary--text">
                {{ item.label }}
              </p>
            </v-card>
          </slide>
        </carousel>
      </client-only>
    </v-responsive>
  </div>
</template>

<script>
import { AREAS } from '@/data/areas'
export default {
  data: () => ({
    options: {
      loop: true,
      autoplay: true,
      autoplayTimeout: 5000,
      paginationColor: '#E1E1E1',
      paginationActiveColor: '#20246E',
      touchDrag: true,
      mouseDrag: true,
      centerMode: true,
    },
    items: AREAS,
  }),

  computed: {
    isPerPage() {
      return this.$vuetify.breakpoint.xsOnly ? 1 : 5
    },
  },

  methods: {
    onDetail(item) {
      this.$router.push(`/areas/${item.slug}`)
    },
  },
}
</script>

<style lang="scss">
.areas__section {
  background: url('/images/areas/bg_area.png');
  background-size: cover;
  background-repeat: no-repeat;

  &__slider {
    width: 100% !important;

    img {
      object-fit: cover !important;
      padding: 0px 10px !important;
      width: 100% !important;
      height: 200px !important;
      transition: all 0.25s ease !important;
      -webkit-transition: all 0.25s ease !important;

      &:hover {
        -webkit-transform: scale(1.05);
        transform: scale(1.05);
      }
    }

    &__label {
      position: absolute;
      bottom: 40px;
      left: 20px;
    }
  }
}
</style>
