<template>
  <v-avatar :color="color" :size="size"
    ><v-icon :color="iconColor">{{ icon }}</v-icon></v-avatar
  >
</template>

<script>
export default {
  props: {
    icon: {
      type: String,
      default: () => 'mdi-close',
    },
    iconColor: {
      type: String,
      default: () => 'dark--text',
    },
    size: {
      type: String,
      default: () => '52',
    },
    color: {
      type: String,
      default: () => 'primary',
    },
  },
}
</script>
