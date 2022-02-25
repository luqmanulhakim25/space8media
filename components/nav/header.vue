<template>
  <div class="navbar">
    <v-app-bar
      height="82"
      fixed
      :color="top ? 'transparent' : 'white'"
      :elevation="top ? 0 : 4"
    >
      <div class="d-flex align-center container">
        <div>
          <v-img max-width="150" :src="isLogo" />
        </div>
        <v-spacer></v-spacer>
        <div
          v-for="(item, index) in items.menu"
          :key="index"
          class="px-8 py-5 hidden-sm-and-down"
          v-scroll-spy-link
          v-scroll-spy-active="{ class: 'navbar__items--active' }"
        >
          <span
            @click="goTo(item.key)"
            class="h6--xsmall pointer navbar__items"
            v-bind:class="{ 'white--text': top, 'dark--text': !top }"
          >
            {{ item.label }}
          </span>
        </div>
      </div>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  data: () => ({
    header_color: '',
    top: true,
    items: {
      menu: [
        { label: 'Home', key: 'hero__section' },
        { label: 'Clients', key: 'clients__section' },
        { label: 'Areas', key: 'areas__section' },
        { label: 'Products', key: 'products__section' },
        { label: 'Why Us', key: 'why-us__section' },
        { label: 'Partners', key: 'partners__section' },
      ],
    },
  }),

  created() {
    if (process.browser) {
      window.addEventListener('scroll', this.handleScroll)
    }
  },

  computed: {
    isLogo() {
      if (this.top) return '/nav-logo-white.png'
      if (!this.top) return '/nav-logo-dark.png'
    },
  },

  methods: {
    handleScroll() {
      if (window.scrollY > 0) {
        this.top = false
      } else {
        this.top = true
      }
      // console.log(window.onscroll)
    },

    goTo(key, index) {
      let options = {
        offset: 100,
      }
      this.$vuetify.goTo(`.${key}`, options)
      // this.state.isActiveTab = index
    },
  },
}
</script>

<style lang="scss" scoped>
.navbar {
  &__items {
    &--active {
      border-bottom: 4px solid var(--v-primary-base);
      color: var(--v-primary-base);
    }
  }
}
</style>
