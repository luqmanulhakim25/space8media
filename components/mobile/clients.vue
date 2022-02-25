<template>
  <div>
    <v-carousel v-model="state.isActiveImage" height="150" hide-delimiters>
      <v-carousel-item v-for="(item, index) in items" :key="index">
        <v-img :src="item" />
      </v-carousel-item>
    </v-carousel>
    <div class="d-flex align-center justify-center">
      <!-- <v-avatar
      class=""
        class="mx-2 mt-4"
        size="16"
        :color="index === state.isActiveImage ? 'red' : 'grey'"
        v-for="(item, index) in items"
        :key="index"
      ></v-avatar> -->
    </div>
  </div>
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

<style lang="scss" scoped></style>
