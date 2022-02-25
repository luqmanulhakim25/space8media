<template>
  <div class="partners__section">
    <v-container class="fill-height fluid">
      <v-row align="center" justify="center">
        <v-col cols="12" class="mt-16">
          <div class="d-flex align-center justify-center flex-column">
            <icon
              icon="mdi-cog"
              color="accent"
              iconColor="white"
              class="mb-4"
            />
            <h2
              class="h2--xlarge primary--text text--darken-1 text-center mb-4"
            >
              Our Partners
            </h2>

            <p
              class="primary--text text--lighten-1 text--large text-center mb-16"
            >
              Lorem Ipsum is simply dummy text of the printing and typesetting
              industry. Lorem Ipsum has <br />
              been the industry's standard dummy text ever since the 1500s,
            </p>
          </div>
        </v-col>
        <v-col
          class="pa-6 hidden-sm-and-down"
          v-bind:class="{
            'partners__section__card__border--bottom': index < 4,
            'partners__section__card__border--right':
              index !== 3 && index !== 7,
          }"
          cols="12"
          md="3"
          v-for="(item, index) in items"
          :key="index"
        >
          <div class="d-flex align-center justify-center">
            <img :src="item.img" alt="logo" />
          </div>
        </v-col>

        <!-- Mobile -->
        <v-col cols="12">
          <mobile-partners :items="items" class="hidden-sm-and-up" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { ITEMS } from '@/data/partners'
export default {
  data: () => ({
    items: ITEMS,
  }),
}
</script>

<style lang="scss" scoped>
.partners__section {
  background: url('/bg-partner.png');
  background-size: cover;
  padding-bottom: 100px;

  &__card {
    &__border--right {
      border-right: 1px solid var(--v-dark-lighten1);
    }

    &__border--bottom {
      border-bottom: 1px solid var(--v-dark-lighten1);
    }
  }
}
</style>
