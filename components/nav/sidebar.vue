<template>
  <v-navigation-drawer
    v-model="state.isDrawer"
    fixed
    temporary
    color="transparent"
    class="container"
  >
    <vs-sidebar absolute open v-model="active_slug">
      <template #logo>
        <v-img max-width="100" src="images/nav-logo-dark.png" class="mr-16" />
      </template>
      <vs-sidebar-item
        :id="item.slug"
        v-for="(item, index) in items.menu"
        :key="index"
      >
        <template #icon>
          <i :class="item.icon" />
        </template>
        <p @click="goTo(item.slug)">
          {{ item.label }}
        </p>
      </vs-sidebar-item>

      <template #footer>
        <vs-button danger icon @click="onInstagram()">
          <v-icon color="white">mdi-instagram</v-icon>
        </vs-button>
      </template>
    </vs-sidebar>
  </v-navigation-drawer>
</template>

<script>
import { MENUS } from '@/data/general'
export default {
  props: {
    state: Object,
  },

  data: () => ({
    items: {
      menu: MENUS,
    },
    active_slug: '/',
  }),

  methods: {
    goTo(slug) {
      this.$router.push(slug)
    },

    onInstagram() {
      let url = 'https://instagram.com/space8media'
      window.open(url)
    },
  },

  watch: {
    $route: {
      handler(val) {
        this.active_slug = val.path
      },
      immediate: true,
    },
  },
}
</script>

<style lang="scss" scoped>
::v-deep .v-navigation-drawer__border {
  background-color: transparent !important;
}

.v-navigation-drawer--is-mobile:not(.v-navigation-drawer--close),
.v-navigation-drawer--temporary:not(.v-navigation-drawer--close) {
  box-shadow: none !important;
}

.vs-sidebar__item.active {
  color: var(--v-primary-base) !important;
}

.vs-sidebar__item:after {
  background: var(--v-primary-base) !important;
}
</style>
