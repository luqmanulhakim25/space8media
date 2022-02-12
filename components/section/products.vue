<template>
  <div
    class="area__section justify-center align-center d-flex flex-column pb-16"
  >
    <icon icon="mdi-cog" color="accent" iconColor="white" class="mb-4" />
    <h2 class="h2--xlarge primary--text text--darken-1 text-center mb-4">
      Our Products
    </h2>

    <p class="primary--text text--lighten-1 text--large text-center mb-10">
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
      Lorem Ipsum has been the <br />
      industry's standard dummy text ever since the 1500s,
    </p>

    <v-row>
      <v-col
        cols="12"
        md="3"
        v-for="(item, index) in items"
        :key="index"
        class="pointer"
      >
        <v-hover v-slot="{ hover }">
          <v-card :class="{ 'on-hover': hover }">
            <v-img :src="item.img">
              <v-container class="fill-height fluid transparent">
                <v-row justify="center" align="center">
                  <v-col cols="12">
                    <!-- <div
                      class="white text-center align-self-center py-2 px-6 d-inline-block"
                    >
                      <p
                        class="h4--default black--text"
                        v-bind:class="{ 'd-none': !hover }"
                      >
                        {{ item.label }}
                      </p>
                    </div> -->
                  </v-col>
                </v-row>
              </v-container>
            </v-img>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data: () => ({
    transparent: 'rgba(255, 255, 255, 0)',
    items: [
      {
        id: 1,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/SCBD-LOT-4-Sudirman-Jakarta_S.webp',
        label: 'Billboard',
      },
      {
        id: 2,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/SCBD-LOT-9-Sudirman-Jakarta_S.webp',
        label: 'Unggul unggul',
      },
      {
        id: 3,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/SCBD-LOT-23-Sudirman-Jakarta_S.webp',
        label: 'Megathron',
      },
      {
        id: 4,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/Iconic-OOH-Soekarno-Hatta-Airport-Tangerang_BARU_S.webp',
        label: 'Billboard',
      },
      {
        id: 5,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2022/01/Sudirman-Bandung.webp',
        label: 'Billboard',
      },
      {
        id: 6,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/Tol-Karang-Tengah-Rest-Area-Tangerang_S.webp',
        label: 'Billboard',
      },
      {
        id: 7,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/Hang-Tuah-Kebayoran-Baru-Jakarta_S.webp',
        label: 'Billboard',
      },
      {
        id: 8,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2022/01/Pillar-Senayan-Ajaib.webp',
        label: 'Billboard',
      },
      {
        id: 9,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/Pluit-Interchange-Tol-Sedyatmo-Jakarta_S.webp',
        label: 'Billboard',
      },
      {
        id: 10,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/Taman-Sari-Cikapayang-Bandung_S.webp',
        label: 'Billboard',
      },
      {
        id: 11,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/Terminal-1-Soekarno-Hatta-Airport-Tangerang_S.webp',
        label: 'Billboard',
      },
      {
        id: 12,
        img: 'https://eyeindonesia.com/eyeadvertising/wp-content/uploads/2019/06/Tol-JLC-Jakarta-Serpong-Bintaro-Jakarta_S.webp',
        label: 'Billboard',
      },
    ],
  }),
}
</script>

<style lang="scss" scoped>
.col-md-3 {
  padding: 0px !important;
}

.v-card {
  transition: opacity 1s, transform 0.5s ease-in-out;
  transform: scale(1.05);
  z-index: 1;
}

.v-card:not(.on-hover) {
  opacity: 0.8;
  transform: scale(1);
  z-index: 0;
}
</style>
