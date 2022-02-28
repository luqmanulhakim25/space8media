<template>
  <v-dialog v-model="dialog" persistent width="475">
    <div class="white rounded-xl pa-6 overflow-hidden">
      <span class="d-flex justify-end pointer"
        ><v-icon color="dark" @click="onEmitClose()">mdi-close</v-icon></span
      >
      <v-img width="150" class="mx-auto" src="/pdf.svg" />

      <vs-input v-model="form.name" block placeholder="Name" class="mt-4">
        <template #icon>
          <i class="bx bx-user"></i>
        </template>
      </vs-input>

      <vs-input
        v-model="form.phone"
        block
        placeholder="Phone"
        class="mt-4"
        @keypress="onDigits"
      >
        <template #icon>
          <i class="bx bx-mobile-alt"></i>
        </template>
      </vs-input>

      <vs-button
        :disabled="!isDisabled"
        block
        class="h7--xxsmall mt-6"
        @click="onDownload()"
        >Download</vs-button
      >
    </div>
  </v-dialog>
</template>

<script>
export default {
  props: {
    dialog: Boolean,
  },

  data: () => ({
    form: {
      name: '',
      phone: '',
    },
  }),

  computed: {
    isDisabled() {
      return this.form.name && this.form.phone
    },
  },

  methods: {
    onDownload() {
      window.open('https://drive.google.com/file/d/1dKRW8-ZFvszPP0HDp_-gvHJSv_n1WXKa/view?usp=sharing')
    },

    onEmitClose() {
      this.$emit('on:close')
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
