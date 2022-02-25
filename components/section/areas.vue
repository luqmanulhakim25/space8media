<template>
  <div
    class="areas__section justify-center align-center d-flex flex-column pb-16"
    v-scroll-spy
  >
    <icon
      icon="mdi-map-marker"
      color="warning lighten-1"
      iconColor="white"
      class="mb-4"
    />
    <h2 class="h2--xlarge primary--text text--darken-1 text-center mb-4">
      Recommended Areas
    </h2>

    <p class="primary--text text--lighten-1 text--large text-center mb-10">
      Produk kami tersebar luas dan menawarkan pengalaman beriklan dengan
      berbagai landmark terkenal di Indonesia, seperti Jakarta, Bandung hingga
      Medan. Jadi, kamu dapat memasang iklan dimana saja
    </p>

    <client-only>
      <carousel v-bind="options">
        <slide
          v-for="(item, index) in items"
          :key="index"
          class="area__section__slider"
        >
          <img :src="item.image" />
          <p class="area__section__title text--large primary--text">
            Tersedia {{ item.availabel }} Media
          </p>
        </slide>
      </carousel>
    </client-only>
  </div>
</template>

<script>
export default {
  data: () => ({
    slides: [
      {
        title: 'Slide #1',
        content: 'Slide content.',
      },
    ],
    options: {
      loop: true,
      perPage: 5,
      paginationEnabled: true,
    },
    items: [
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
      { id: 1, availabel: 30, label: 'Jakarta', image: '/areas/jakarta.png' },
    ],
  }),
}
</script>

<style lang="scss">
.area__section {
  background: url('/bg-area.png');
  background-size: cover;
  background-repeat: no-repeat;

  &__slider {
    img {
      object-fit: contain;
      padding: 0px 40px;
      width: 100%;
      height: 100%;
    }
  }

  &__title {
    position: absolute;
    right: 10px;
    bottom: 10px;
  }
}
</style>
