<template>
  <div class="hidden-sm-and-up container mobile__why--us">
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
                  class="why-us__section__card rounded-xl pa-6 mb-6 transparent"
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
                    >mdi-wallet</v-icon
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
                <v-card class="rounded-xl pa-6 transparent">
                  <v-icon size="62" color="primary" class="mb-4"
                    >mdi-briefcase-variant-outline</v-icon
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
  </div>
</template>

<style lang="scss" scoped>
.mobile__why--us {
  background-image: url('/bg_mobile-why-us.png');
  background-size: cover;
  height: auto;
  background-repeat: no-repeat;
}
</style>
