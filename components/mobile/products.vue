<template>
  <vs-card type="2" class="mt-2 mt-md-0">
    <template #title>
      <h3 class="h4--default">{{ item.label }}</h3>
    </template>
    <template #img>
      <v-img width="100%" :src="item.img" alt="" />
    </template>
    <!-- <template #text>
            <v-card flat class="py-2 px-4">
            </v-card>
          </template> -->
    <template #text>
      <p class="text--default">
        Jl. Raya Parung (Setelah Warung Sate Solo Tiga Saudara) – Depok
      </p>
    </template>
    <template #interactions>
      <!-- <vs-button danger icon>
              <i class="bx bx-heart"></i>
            </vs-button> -->
      <!-- <vs-button class="btn-chat" shadow primary>
              <v-icon>mdi-eye</v-icon>
              <span class="span"> Billboard </span>
            </vs-button> -->
    </template>
  </vs-card>
</template>

<script>
export default {
  props: {
    item: Object,
  },
}
</script>
