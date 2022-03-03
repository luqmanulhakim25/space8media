<template>
  <div class="contact">
    <v-card flat color="primary darken-3" height="82" width="100%"></v-card>
    <v-container py-16>
      <v-row>
        <v-col cols="12">
          <div class="d-flex align-center justify-center flex-column">
            <icon
              color="primary lighten-2"
              iconColor="white"
              class="mb-4"
              icon="mdi-email-fast-outline"
            />
            <h2
              class="h2--xlarge primary--text text--darken-1 text-center mb-4"
            >
              Contact Us
            </h2>
            <v-responsive width="800">
              <p
                class="primary--text text--lighten-1 text--large text-center mb-sm-16 px-4"
              >
                Our products are widely distributed and offer an advertising
                experience with various famous landmarks in Indonesia, such as
                Jakarta, Bandung to Medan. So, you can place ads anywhere
              </p>
            </v-responsive>
          </div>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="7" align-self="center">
          <v-img
            class="contact__image mx-auto"
            src="/images/contact/vector.svg"
          />
        </v-col>
        <v-col cols="12" sm="5" align-self="center">
          <div class="white contact__card pa-8 rounded-xl">
            <vs-input v-model="form.name" block label-placeholder="Name">
              <template #icon>
                <i class="bx bx-user"></i>
              </template>
            </vs-input>

            <vs-input
              v-model="form.email"
              block
              label-placeholder="Email"
              class="mt-6"
            >
              <template #icon>
                <i class="bx bx-envelope"></i>
              </template>
            </vs-input>

            <vs-input
              v-model="form.phone"
              block
              label-placeholder="Phone"
              class="mt-6"
              @keypress="onDigits"
            >
              <template #icon>
                <i class="bx bx-mobile"></i>
              </template>
            </vs-input>

            <vs-button
              block
              warn
              size="large"
              class="h7--xxsmall mt-6 primary--text"
            >
              Submit
            </vs-button>
            <div />
          </div>
        </v-col>
      </v-row>
    </v-container>
    <v-img />

    <div
      class="contact__recommendation_areas d-flex align-center justify-center flex-column"
    >
      <h3 class="h3--large white--text text-center mb-4">
        Looking for recommendation areas?
      </h3>
      <v-btn
        outlined
        depressed
        dark
        class="text-capitalize h7--xxsmall rounded-xl"
        @click="onAreas()"
        >Click Here</v-btn
      >
    </div>

    <div class="contact__maps primary darken-3">
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3964.996788501078!2d106.81217041476998!3d-6.3944142953732035!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e69e95313e929b3%3A0x5c16dff1e5e8b23!2sKoti!5e0!3m2!1sen!2sid!4v1646229330167!5m2!1sen!2sid"
        class="full-width"
        height="500"
        style="border: 0"
        loading="lazy"
      />
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    form: {
      name: '',
      email: '',
      phone: '',
    },
  }),

  methods: {
    onAreas() {
      this.$router.push('/areas')
    },

    onDigits(event) {
      let keyCode = event.keyCode
      if (keyCode < 48 || keyCode > 57) {
        event.preventDefault()
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.contact {
  &__image {
    width: 500px;
    @media (max-width: 599px) {
      width: 300px;
    }
    @media (min-width: 600px) and (max-width: 960px) {
      width: 400px;
    }
  }

  &__card {
    box-shadow: 0px 12px 26px rgba(0, 69, 172, 0.14) !important;
  }

  &__recommendation_areas {
    background: url('/images/contact/bg_contact.svg');
    background-attachment: fixed;
    background-size: cover;
    background-repeat: no-repeat;
    @media (min-width: 1264px) {
      height: 60vh;
    }
    @media (max-width: 960px) {
      background-size: auto;
      background-attachment: unset;
      height: 60vh;
    }
  }
}
</style>
