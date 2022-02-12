<template>
  <div class="hero__section d-flex flex-column align-center">
    <v-container class="fill-height fluid">
      <v-row align="center" justify="center" no-gutters>
        <v-col cols="12" md="5">
          <v-card flat color="transparent">
            <p class="hero__section__title white--text">Space 8 Media</p>
            <p class="hero__section__description white--text">
              Loremipsumdolorsitamet,consectetur adipiscingelit <br />
              Loremipsumdolorsitamet,consectetur
            </p>
            <v-btn outlined dark large class="rounded-xl mt-6"> Explore </v-btn>
          </v-card>
        </v-col>
        <v-col cols="12" md="7">
          <v-slide-group dark v-model="model">
            <v-slide-item
              v-for="(item, index) in items.products"
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
            </v-slide-item> </v-slide-group
        ></v-col>

        <v-col cols="12" md="10"
          ><div class="mt-6 ml-2">
            <v-icon size="36" color="white" class="mr-2">mdi-facebook</v-icon>
            <v-icon size="36" color="white" class="mr-2">mdi-instagram</v-icon>
            <v-icon size="36" color="white">mdi-twitter</v-icon>
          </div></v-col
        >
        <v-col cols="12" md="2" class="pl-16">
          <v-icon size="42" color="white"
            >mdi-chevron-left-circle-outline</v-icon
          >
          <v-icon size="42" color="yellow"
            >mdi-chevron-right-circle-outline</v-icon
          >
        </v-col>
      </v-row>
    </v-container>

    <wheel />
  </div>
</template>

<script>
export default {
  data: () => ({
    model: null,
    items: {
      products: [
        { id: 1, src: '/hero/product-1.png' },
        { id: 2, src: '/hero/product-2.png' },
        { id: 3, src: '/hero/product-3.png' },
      ],
    },
  }),
}
</script>

<style lang="scss" scoped>
.hero__section {
  background: url('/hero.jpg');
  background-attachment: fixed;
  background-size: cover;
  height: 100vh;

  &:before {
    content: '';
    width: 100%;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.4);
    position: absolute;
  }

  &__title {
    font-size: 62px;
  }

  &__description {
    font-size: 24px;
  }
}
</style>
