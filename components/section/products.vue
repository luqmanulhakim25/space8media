<template>
  <div
    class="products__section justify-center align-center d-flex flex-column pb-16"
    v-scroll-spy
  >
    <icon icon="mdi-cog" color="accent" iconColor="white" class="mb-4" />
    <h2 class="h2--xlarge primary--text text--darken-1 text-center mb-4">
      Our Products
    </h2>

    <p class="primary--text text--lighten-1 text--large text-center mb-10">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
      Lorem Ipsum has been the <br />
      industry's standard dummy text ever since the 1500s,
    </p>

    <v-row class="pointer hidden-sm-and-down">
      <v-col
        cols="12"
        md="3"
        xl="2"
        v-for="(item, index) in items"
        :key="index"
      >
        <!-- <v-hover v-slot="{ hover }">
          <v-card :class="{ 'on-hover': hover }">
            <v-img :src="item.img">
              <v-container class="fill-height fluid transparent">
                <v-row justify="center" align="center">
                  <v-col cols="12">
                    <div
                      class="white text-center align-self-center py-2 px-6 d-inline-block"
                    >
                      <p
                        class="h4--default black--text"
                        v-bind:class="{ 'd-none': !hover }"
                      >
                        {{ item.label }}
                      </p>
                    </div>
                  </v-col>
                </v-row>
              </v-container>
            </v-img>
          </v-card>
        </v-hover> -->

        <vs-card type="2">
          <template #title>
            <h3>Pot with a plant</h3>
          </template>
          <template #img>
            <img :src="item.img" alt="" />
          </template>
          <template #text>
            <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit.</p>
          </template>
          <!-- <template #interactions>
                    <vs-button danger icon>
                      <i class="bx bx-heart"></i>
                    </vs-button>
                    <vs-button class="btn-chat" shadow primary>
                      <i class="bx bx-chat"></i>
                      <span class="span"> 54 </span>
                    </vs-button>
                  </template> -->
        </vs-card>
      </v-col>
    </v-row>

    <mobile-products :items="items" class="hidden-sm-and-up" />
  </div>
</template>

<script>
import { ITEMS } from '@/data/products'
export default {
  data: () => ({
    items: ITEMS,
    transparent: 'rgba(255, 255, 255, 0)',
  }),
}
</script>

<style lang="scss" scoped>
.col-md-3 {
  padding: 0px !important;
}

.v-card {
  transition: opacity 1s, transform 0.5s ease-in-out;
  transform: scale(1.05);
  z-index: 1;
}

.v-card:not(.on-hover) {
  opacity: 0.8;
  transform: scale(1);
  z-index: 0;
}
</style>
