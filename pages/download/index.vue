<template>
  <div class="download">
    <v-card color="primary" height="82" flat></v-card>
    <v-container fill-height fluid>
      <v-row align="center" justify="center">
        <v-col cols="12">
          <v-text-field
            v-model="form.name"
            label="name"
            outlined
          ></v-text-field>
          <v-text-field
            v-model="form.phone"
            label="phone"
            outlined
          ></v-text-field>
          <v-btn color="primary" @click="onSubmit()">Submit</v-btn>
          <br />
          {{ phone }}
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { PHONE } from '@/data/customers'
export default {
  data: () => ({
    phone: PHONE,
    form: {
      name: '',
      phone: '',
    },
  }),

  methods: {
    onSubmit() {
      let date = new Date()
      this.phone.push({
        date: date,
        name: this.form.name,
        phone: this.form.phone,
      })
    },
  },
}
</script>

<style lang="scss" scoped>
.download {
  height: 100vh;
}
</style>
