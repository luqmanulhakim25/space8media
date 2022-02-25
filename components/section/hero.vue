<template>
  <div class="hero__section d-flex flex-column align-center" v-scroll-spy>
    <v-container class="fill-height fluid">
      <v-row align="center" justify="center">
        <v-col cols="12" md="5">
          <v-card flat color="transparent">
            <p class="hero__section__title white--text">Space 8 Media</p>
            <p class="hero__section__description white--text">
              We develop a combination of ability, reliability and creativity of
              resources to achieve professional work, in order to support our
              services as well as the success of our clients and working
              partners
            </p>
            <vs-button outlined size="large" class="h7--xxsmall mt-6">
              Explore
            </vs-button>
            <v-btn outlined dark large class="rounded-xl mt-6 d-none">
              Explore
            </v-btn>
          </v-card>
        </v-col>
        <v-col cols="12" md="7">
          <v-slide-group
            dark
            v-model="state.isActiveImage"
            class="hidden-sm-and-down"
          >
            <v-slide-item
              v-for="(item, index) in items"
              :key="index"
              v-slot="{ active, toggle }"
              value="3"
            >
              <v-card
                :color="active ? undefined : 'grey lighten-1'"
                class="ma-4"
                height="auto"
                width="200"
                @click="toggle"
              >
                <v-img :src="item.src"></v-img>
              </v-card>
            </v-slide-item>
          </v-slide-group>

          <v-carousel
            v-model="state.isActiveImage"
            class="hidden-sm-and-up mt-6"
            height="400"
          >
            <v-carousel-item v-for="(item, index) in items" :key="index">
              <v-img :src="item.src"></v-img>
            </v-carousel-item>
          </v-carousel>
        </v-col>

        <v-col cols="12"
          ><div class="mt-6 ml-2">
            <v-icon size="36" color="white" class="mr-2">mdi-instagram</v-icon>
          </div></v-col
        >
      </v-row>
    </v-container>
    <wheel />
  </div>
</template>

<script>
import { ITEMS } from '@/data/hero'
export default {
  data: () => ({
    fab: false,
    hidden: false,
    tabs: null,
    state: {
      isActiveImage: 0,
    },
    items: ITEMS,
  }),
}
</script>

<style lang="scss" scoped>
.hero__section {
  background: url('/hero.jpg');
  background-attachment: fixed;
  background-size: cover;
  height: 100vh;
  @media (max-width: 600px) {
    height: auto;
  }

  &:before {
    content: '';
    width: 100%;
    height: 100vh;
    background-color: rgba(34, 40, 85, 0.4);
    position: absolute;
    @media (max-width: 600px) {
      height: auto;
    }
  }

  &__title {
    font-size: 62px;
    @media (max-width: 600px) {
      font-size: 42px;
      margin-top: 64px;
    }
  }

  &__description {
    font-size: 18px;
    @media (max-width: 600px) {
      font-size: 18px;
    }
  }
}
::v-deep .vs-button--size-large .vs-button__content {
  padding: 10px 30px;
}
</style>
