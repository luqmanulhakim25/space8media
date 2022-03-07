<template>
  <div class="hero__section d-flex flex-column align-center">
    <v-container fill-height fluid class="mt-16 px-6 px-md-0">
      <v-row align="center" justify="center" no-gutters>
        <v-col cols="12">
          <v-img
            width="100"
            src="/images/hero/mars.svg"
            class="hero__section__mars bounce"
          />
        </v-col>
        <v-col cols="12">
          <v-img
            width="110"
            src="/images/hero/moon.svg"
            class="hero__section__moon bounce-moon"
          />
        </v-col>
        <v-col cols="auto" md="8">
          <v-card
            flat
            class="hero__section__card mx-auto d-flex flex-column align-center py-8 px-md-16 px-4"
            data-aos="fade-up"
            data-aos-duration="800"
          >
            <p class="hero__section__title secondary--text">Space 8 Media</p>
            <p class="hero__section__description white--text text-center">
              We develop a combination of ability, reliability and creativity of
              resources to achieve professional work, in order to support our
              services as well as the success of our clients and working
              partners
            </p>

            <vs-input
              v-model="search"
              block
              placeholder="Find location"
              class="mt-8"
              @keypress.enter="onSearch()"
            >
              <template #icon>
                <v-icon>mdi-magnify</v-icon>
              </template>
              <template #message-danger v-if="!valid">
                Type location here
              </template>
            </vs-input>

            <vs-button
              block
              warn
              size="large"
              class="h7--xxsmall mt-4 primary--text"
              @click="onSearch()"
            >
              Explore
              <v-icon color="primary" class="ml-2"
                >mdi-arrow-right-circle</v-icon
              >
            </vs-button>
            <v-card class="d-none" />
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <wheel @on:goTo="goTo" class="mt-6 mt-md-0" />
  </div>
</template>

<script>
import { ITEMS } from '@/data/hero'
export default {
  data: () => ({
    search: '',
    valid: true,
    state: {
      isActiveImage: 0,
    },
    items: ITEMS,
  }),

  mounted() {
    this.$vs.setColor('warn', '#FDF103')
  },

  methods: {
    onSearch() {
      if (!this.search) {
        this.valid = false
      }

      if (this.search) {
        this.$router.push({ path: '/areas', hash: this.search })
      }
    },

    goTo() {
      let options = {
        offset: 0,
      }
      let target = '.clients__section'
      this.$vuetify.goTo(target, options)
    },
  },

  watch: {
    search: {
      handler(val) {
        if (val) {
          this.valid = true
        }
      },
    },
    immediate: true,
  },
}
</script>

<style lang="scss" scoped>
.hero__section {
  background: url('/images/hero/bg_space.svg');
  background-color: #1d224c !important;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
  height: 100vh;

  @media (max-width: 960px) {
    background-attachment: unset;
    height: auto;
  }

  @media (max-width: 600px) {
    background-attachment: unset;
    height: 100vh;
  }

  &:before {
    content: '';
    width: auto;
    height: 100vh;
    background-color: rgba(17, 17, 31, 0.4);
    position: absolute;
    @media (max-width: 600px) {
      height: 100vh;
    }
  }

  &__card {
    border-radius: 16px !important;
    background-color: #1d1f36 !important;

    @media (max-width: 960px) {
      margin-top: 32px;
    }
  }

  &__title {
    font-size: 62px;
    font-weight: 600;
    @media (max-width: 600px) {
      font-size: 32px !important;
    }
    @media (max-width: 960px) {
      font-size: 52px;
    }
  }

  &__description {
    font-size: 16px;
  }
}

.hero__section__mars {
  animation-duration: 10s;
  animation-iteration-count: infinite;
  transform-origin: bottom;
  @media (min-width: 1264px) and (max-width: 1904px) {
    position: absolute;
    top: 300px;
  }
}

.bounce {
  animation-name: bounce;
  animation-timing-function: linear;
}

@keyframes bounce {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-50px);
  }
  100% {
    transform: translateY(0);
  }
}

.hero__section__moon {
  position: absolute;
  right: 300px;
  top: 500px;
  animation-duration: 10s;
  animation-iteration-count: infinite;
  transform-origin: bottom;
}

.bounce-moon {
  animation-name: bounce-moon;
  animation-timing-function: linear;
}

@keyframes bounce-moon {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-50px);
  }
  100% {
    transform: translateY(0);
  }
}
</style>
