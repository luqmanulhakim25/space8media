<template>
  <div>
    <v-app-bar
      height="82"
      fixed
      :color="top ? 'transparent' : 'white'"
      elevation="3"
    >
      <div class="d-flex align-center container">
        <div>
          <v-img max-width="150" :src="isLogo" />
        </div>
        <!-- src="https://sis-dev-public.s3.amazonaws.com/s8-1644068016266.png" -->
        <v-spacer></v-spacer>
        <div
          v-for="(item, index) in items.menu"
          :key="index"
          class="px-8 py-5 hidden-sm-and-down"
        >
          <span
            class="h6--xsmall pointer"
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
        { id: 1, label: 'Home' },
        { id: 2, label: 'Area' },
        { id: 3, label: 'Products' },
        { id: 4, label: 'Why us' },
        { id: 5, label: 'Partners' },
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
    },
  },
}
</script>
