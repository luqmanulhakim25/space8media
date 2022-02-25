<template>
  <div>
    <VueSlickCarousel class="carousel-container">
      <div v-for="(item, i) in 3" :key="i">
        <v-card width="100" height="100">{{ i }}</v-card>
      </div>
    </VueSlickCarousel>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
  components: { VueSlickCarousel },
}
</script>
