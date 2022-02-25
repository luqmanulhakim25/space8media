<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-carousel v-model="state.isActiveImage" height="200" hide-delimiters>
          <v-carousel-item v-for="(item, index) in items" :key="index">
            <v-img :src="item.img" />
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: {
    isActiveImage: Number,
    items: Array,
  },

  data: () => ({
    state: {
      isActiveImage: 0,
    },
  }),
}
</script>
