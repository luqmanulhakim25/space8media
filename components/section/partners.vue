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
              class="primary--text text--lighten-1 text--large text-center mb-md-16 px-4"
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
          sm="3"
          v-for="(item, index) in items"
          :key="index"
        >
          <div class="d-flex align-center justify-center">
            <v-img max-width="150" :src="item.img" alt="logo" />
          </div>
        </v-col>
      </v-row>

      <v-row align="center" justify="center">
        <!-- Mobile -->
        <v-col
          cols="auto"
          v-for="(item, index) in items"
          :key="index"
          class="hidden-md-and-up"
        >
          <v-img max-width="150" :src="item.img" alt="logo" />
        </v-col>
        <!-- END MOBILE -->
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
  background: url('/images/partners/bg-partner.png');
  background-size: cover;
  padding-bottom: 100px;
  @media (max-width: 960px) {
    padding-bottom: 50px;
  }

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
