<template>
  <div class="area__section hidden-lg-and-up py-16">
    <icon
      color="primary lighten-1"
      iconColor="white"
      class="mb-4 d-flex align-center justify-center mx-auto"
      icon="mdi-map-marker-outline"
    />
    <h2 class="h2--xlarge primary--text text--darken-1 text-center mb-4">
      Recommended Areas
    </h2>
    <v-responsive width="800" class="mx-auto">
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
            class="area__section__slider"
          >
            <v-responsive>
              <img :src="item.image" class="pointer" @click="onDetail(item)" />
              <v-card
                flat
                class="area__section__slider__label d-inline-block px-4"
              >
                <p class="h7--xxsmall primary--text text-capitalize">
                  {{ item.slug }}
                </p>
              </v-card>
            </v-responsive>
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
      mouseDrag: true,
    },
    items: AREAS,
  }),

  computed: {
    isPerPage() {
      if (this.$vuetify.breakpoint.xsOnly) return 2
      if (this.$vuetify.breakpoint.sm) return 3
      if (this.$vuetify.breakpoint.md) return 5
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
.area__section {
  background: url('/bg-area.png');
  background-size: cover;
  background-repeat: no-repeat;

  &__slider {
    width: 100%;

    img {
      object-fit: cover;
      padding: 0px 10px;
      width: 100%;
      height: 200px;
      transition: all 0.25s ease;
      -webkit-transition: all 0.25s ease;

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
