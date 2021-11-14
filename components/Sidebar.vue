<template></template>

<script>
export default {
  props: ['drawer', 'miniVariant'],
  watch: {
    drawer: function (newQuestion, oldQuestion) {
      this.navDrawer = newQuestion
    },
  },
  data: () => ({
    navDrawer: false,
    items: [
      {
        icon: 'mdi-apps',
        title: 'Welcome',
        to: '/',
      },
      {
        icon: 'mdi-chart-bubble',
        title: 'Inspire',
        to: '/inspire',
      },
    ],
  }),
}
</script>

<style></style>
