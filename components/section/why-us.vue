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
                class="primary--text text--lighten-1 text--large text-center mb-16"
              >
                Lorem Ipsum is simply dummy text of the printing and typesetting
                industry. Lorem Ipsum has <br />
                been the industry's standard dummy text ever since the 1500s,
              </p>
            </div>
          </v-col>
          <v-col cols="12" md="5" class="pb-16">
            <v-img src="/why-us-billboard.png" />
          </v-col>
          <v-col cols="12" md="6" class="pb-16">
            <v-container>
              <v-row>
                <v-col cols="12" md="6">
                  <v-card
                    class="why-us__section__card rounded-xl pa-6 mb-6 ml-n6 transparent"
                  >
                    <v-icon size="62" color="primary" class="mb-4"
                      >mdi-hand-heart-outline</v-icon
                    >
                    <p class="primary--text h5--small mb-2">Lorem ipsum</p>
                    <p class="primary--text text--lighten-1 text--large">
                      Lorem Ipsum is simply dummy text of the printing and
                      typesetting industry. Lorem Ipsum has been the industry's
                      standard dummy text ever since the 1500s,
                    </p>
                  </v-card>
                  <v-card class="rounded-xl pa-6 transparent">
                    <v-icon size="62" color="primary" class="mb-4"
                      >mdi-hand-heart-outline</v-icon
                    >
                    <p class="primary--text h5--small mb-2">Lorem ipsum</p>
                    <p class="primary--text text--lighten-1 text--large">
                      Lorem Ipsum is simply dummy text of the printing and
                      typesetting industry. Lorem Ipsum has been the industry's
                      standard dummy text ever since the 1500s,
                    </p>
                  </v-card>
                </v-col>
                <v-col cols="12" md="6">
                  <v-card class="rounded-xl pa-6 mt-16 transparent">
                    <v-icon size="62" color="primary" class="mb-4"
                      >mdi-hand-heart-outline</v-icon
                    >
                    <p class="primary--text h5--small mb-2">Lorem ipsum</p>
                    <p class="primary--text text--lighten-1 text--large">
                      Lorem Ipsum is simply dummy text of the printing and
                      typesetting industry. Lorem Ipsum has been the industry's
                      standard dummy text ever since the 1500s,
                    </p>
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

<style lang="scss" scoped>
.why-us__section {
  background: url('/bg-why-us.png');
  background-size: cover;
  height: auto;

  &__container {
    background-image: url('/why-us-card.png');
    background-size: cover;
    background-repeat: no-repeat;
    padding-top: 100px;
    @media (min-width: 1904px) {
      height: 150vh;
    }
    @media (min-width: 1264px) and (max-width: 1904px) {
      height: 120vh;
      margin: 0 auto;
    }
  }
}
</style>
