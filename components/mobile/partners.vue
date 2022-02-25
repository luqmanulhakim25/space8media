<template>
  <v-carousel v-model="state.isActiveImage" height="150" hide-delimiters>
    <v-carousel-item v-for="(item, index) in items" :key="index">
      <v-img :src="item.img" />
    </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  props: {
    items: Array,
  },
  data: () => ({
    state: {
      isActiveImage: 0,
    },
  }),
}
</script>
