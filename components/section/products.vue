<template>
  <div
    class="products__section justify-center align-center d-flex flex-column pb-16"
  >
    <icon icon="mdi-cog" color="accent" iconColor="white" class="mb-4" />
    <h2 class="h2--xlarge primary--text text--darken-1 text-center mb-4">
      Our Products
    </h2>

    <v-responsive width="800">
      <p
        class="primary--text text--lighten-1 text--large text-center mb-10 px-4"
      >
        Lorem Ipsum is simply dummy text of the printing and typesetting
        industry. Lorem Ipsum has been the industry's standard dummy text ever
        since the 1500s,
      </p>
    </v-responsive>

    <v-row class="pointer hidden-xs-only">
      <v-col
        cols="12"
        md="3"
        xl="2"
        sm="4"
        v-for="(item, index) in items"
        :key="index"
      >
        <v-responsive>
          <vs-card type="2">
            <template #title>
              <h3 class="h4--default">{{ item.label }}</h3>
            </template>
            <template #img>
              <v-img width="100%" :src="item.img" alt="" />
            </template>
            <!-- <template #text>
            <v-card flat class="py-2 px-4">
            </v-card>
          </template> -->
            <template #text>
              <p class="text--default">
                Jl. Raya Parung (Setelah Warung Sate Solo Tiga Saudara) – Depok
              </p>
            </template>
            <template #interactions>
              <!-- <vs-button danger icon>
              <i class="bx bx-heart"></i>
            </vs-button> -->
              <!-- <vs-button class="btn-chat" shadow primary>
              <v-icon>mdi-eye</v-icon>
              <span class="span"> Billboard </span>
            </vs-button> -->
            </template>
          </vs-card>
        </v-responsive>
      </v-col>
    </v-row>

    <!-- MOBILE -->
    <mobile-products
      class="hidden-sm-and-up"
      v-for="(item, index) in items"
      :key="index"
      :item="item"
    />
    <!-- END MOBILE -->
  </div>
</template>

<script>
import { PRODUCTS } from '@/data/products'
export default {
  data: () => ({
    items: PRODUCTS,
    transparent: 'rgba(255, 255, 255, 0)',
  }),
}
</script>

<style lang="scss" scoped>
.col-md-3 {
  padding: 0px !important;
}

::v-deep .vs-card__img {
  border-radius: 0px !important;
  &:hover {
    opacity: 1;
  }
}

::v-deep .vs-card {
  border-radius: 0px !important;
  background: none !important;
}

::v-deep .vs-card-content.type-2 .vs-card__text {
  padding-top: 100px;
}
</style>
