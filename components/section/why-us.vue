<template>
  <div class="why-us__section mx-auto">
    <v-card flat class="why-us__section__container">
      <v-container fill-height fluid>
        <v-row align="center" justify="center">
          <v-col cols="12">
            <div class="d-flex align-center flex-column">
              <icon
                icon="mdi-cog"
                color="accent"
                iconColor="white"
                class="mb-4"
              />
              <h2
                class="h2--xlarge primary--text text--darken-1 text-center mb-4"
              >
                Why Us?
              </h2>

              <p
                class="primary--text text--darken-1 text--large text-center mb-16 px-4"
              >
                We aim to give the best services by prioritizing quality,
                creativity, and professionalism, in order to provide our <br />
                customer with satisfaction so we could become a company that is
                well reputed and able to compete with other national companies
                <br />
                throughout Indonesia and also with multi-national companies in
                the future.
              </p>
            </div>
          </v-col>
          <v-col cols="12" md="5" sm="5" class="pb-16">
            <v-img src="/images/why-us/why-us-billboard.png" />
          </v-col>
          <v-col cols="12" md="6" class="pb-16">
            <v-container>
              <v-row>
                <v-col
                  cols="12"
                  md="6"
                  sm="6"
                  v-for="(item, index) in items"
                  :key="index"
                >
                  <v-card
                    class="why-us__section__card pa-6 d-flex flex-column align-center align-md-start full-height"
                    flat
                  >
                    <v-avatar :color="item.icon_color" size="62" class="mb-6">
                      <v-icon size="42" color="white" class="mb-4 my-auto">{{
                        item.icon
                      }}</v-icon>
                    </v-avatar>
                    <div>
                      <p
                        class="primary--text h5--small mb-2 text-center text-md-left"
                      >
                        {{ item.title }}
                      </p>
                      <p class="primary--text text--lighten-1 text--large">
                        {{ item.description }}
                      </p>
                    </div>
                  </v-card>
                </v-col>
              </v-row>
            </v-container>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </div>
</template>

<script>
import { WHY_US } from '@/data/why-us'
export default {
  data: () => ({
    items: WHY_US,
  }),
}
</script>

<style lang="scss" scoped>
.why-us__section {
  background: url('/images/why-us/bg-why-us.png');
  background-size: cover;
  height: auto;

  &__container {
    background-image: url('/images/why-us/why-us-card.png');
    background-size: cover;
    background-repeat: no-repeat;
    padding-top: 100px;
    @media (min-width: 1904px) {
      height: 150vh;
      padding-top: 0px;
    }
    @media (min-width: 1264px) and (max-width: 1904px) {
      height: auto;
      margin: 0 auto;
      background-size: 100% 100%;
      padding-bottom: 80px;
    }
    @media (min-width: 200px) and (max-width: 960px) {
      padding-top: 40px;
      background-image: url('/images/why-us/bg_mobile-why-us.png');
    }
  }

  &__card {
    transition: all 0.25s ease;
    box-shadow: 0px 5px 20px 0px rgba(0, 0, 0, var(--vs-shadow-opacity)) !important;
    border-radius: 20px !important;
    &:hover {
      transform: translate(0, 5px);
    }
  }
}
</style>
