<template>
  <div
    class="areas__section justify-center align-center d-flex flex-column pb-16"
  >
    <icon
      color="primary lighten-1"
      iconColor="white"
      class="mb-4"
      icon="mdi-map-marker-outline"
      data-aos="fade-up"
    />
    <h2
      class="h2--xlarge primary--text text--darken-1 text-center mb-8"
      data-aos="fade-up"
    >
      Areas
    </h2>

    <v-responsive>
      <client-only>
        <carousel v-bind="options" :perPage="isPerPage">
          <slide
            v-for="(item, index) in items"
            :key="index"
            class="areas__section__slider"
            data-aos="fade-left"
          >
            <img :src="item.image" class="pointer" @click="onDetail(item)" />
            <v-card
              flat
              class="areas__section__slider__label d-inline-block px-4"
            >
              <p class="h7--xxsmall primary--text text-capitalize">
                {{ item.slug }}
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
      return this.$vuetify.breakpoint.xsOnly ? 2 : 5
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
