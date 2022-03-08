<template>
  <div class="download">
    <v-card color="primary" height="82" flat></v-card>
    <v-container fill-height fluid>
      <v-row align="center" justify="center">
        <ul>
          <li v-for="(item, index) in users" :key="index">
            {{ item.name }}
          </li>
        </ul>
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
          <v-btn color="primary" @click="onPost()">Post</v-btn>
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
    users: [],
    form: {
      name: '',
      phone: '',
    },
  }),

  methods: {
    onSubmit() {
      this.$axios.get('http://127.0.0.1:8000/api/customers').then((r) => {
        this.users = r.data
        console.log(r)
      })

      // let date = new Date()
      // this.phone.push({
      //   date: date,
      //   name: this.form.name,
      //   phone: this.form.phone,
      // })
    },

    onPost() {
      this.$axios
        .post('http://127.0.0.1:8000/api/customers', this.form)
        .then((r) => {
          console.log(r)
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
