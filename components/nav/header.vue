<template>
  <div class="navbar">
    <v-app-bar
      height="82"
      fixed
      :color="state.isTop ? 'transparent' : 'white'"
      :elevation="state.isTop ? 0 : 4"
    >
      <div class="d-flex align-center container">
        <div>
          <v-img
            max-width="150"
            class="pointer"
            :src="isLogo"
            @click="onHome()"
          />
        </div>
        <v-spacer></v-spacer>
        <div
          v-for="(item, index) in items.menu"
          :key="index"
          class="navbar__menu px-8 py-5 hidden-xs-only"
          v-bind:class="{
            'navbar__menu--active__top':
              state.isActiveSlug === item.slug && state.isTop,
            'navbar__menu--active':
              state.isActiveSlug === item.slug && !state.isTop,
          }"
        >
          <span
            @click="goTo(item.slug)"
            class="h6--xsmall pointer"
            v-bind:class="{
              'white--text': state.isTop && state.isActiveSlug !== item.slug,
              'dark--text': !state.isTop && state.isActiveSlug !== item.slug,
              'secondary--text':
                state.isActiveSlug === item.slug && state.isTop,
              'primary--text': state.isActiveSlug === item.slug && !state.isTop,
            }"
          >
            {{ item.label }}
          </span>
        </div>
        <v-icon
          size="26"
          :color="state.isTop ? 'white' : 'dark'"
          class="pointer hidden-xs-only mt-1"
          @click="onInstagram()"
          >mdi-instagram</v-icon
        >
        <v-btn
          depressed
          outlined
          @click.stop="state.isDrawer = !state.isDrawer"
          class="rounded-xl hidden-sm-and-up"
          :color="state.isTop ? 'white' : 'dark'"
        >
          <v-icon>mdi-menu</v-icon>
        </v-btn>
      </div>
    </v-app-bar>

    <!-- SIDEBAR -->
    <nav-sidebar :state="state" />
    <!-- END SIDEBAR -->
  </div>
</template>

<script>
import { MENUS } from '@/data/general'
export default {
  data: () => ({
    state: {
      isDrawer: false,
      isTop: true,
      isActiveSlug: '',
    },
    items: {
      menu: MENUS,
    },
  }),

  created() {
    if (process.browser) {
      window.addEventListener('scroll', this.handleScroll)
    }
  },

  computed: {
    isLogo() {
      if (this.state.isTop) return '/nav-logo-white.png'
      if (!this.state.isTop) return '/nav-logo-dark.png'
    },
  },

  methods: {
    handleScroll() {
      if (window.scrollY > 0) {
        this.state.isTop = false
      } else {
        this.state.isTop = true
      }
    },

    goTo(slug) {
      this.$router.push(slug)
    },

    onHome() {
      let path = this.$route.path
      if (path === '/') {
        let options = {
          offset: 0,
        }
        this.$vuetify.goTo('.hero__section ', options)
      } else {
        this.$router.push('/')
      }
    },

    onInstagram() {
      let url = 'https://instagram.com/space8media'
      window.open(url)
    },
  },

  watch: {
    $route: {
      handler(val) {
        this.state.isActiveSlug = val.path
      },
      immediate: true,
    },
  },
}
</script>

<style lang="scss" scoped>
.navbar {
  &__menu {
    &--active__top {
      border-bottom: 1px solid var(--v-secondary-base);
    }

    &--active {
      border-bottom: 3px solid var(--v-primary-base);
    }
  }
}
</style>
