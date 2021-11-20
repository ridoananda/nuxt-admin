<template>
  <v-navigation-drawer
    v-model="drawerValue"
    @input="input"
    :mini-variant="miniVariant"
    fixed
    app
    :permanent="$vuetify.breakpoint.mdAndUp"
  >
    <v-list>
      <v-list-item
        v-for="(item, i) in items"
        :key="i"
        :to="item.to"
        router
        exact
      >
        <v-list-item-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title v-text="item.title" />
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  props: ['drawer', 'miniVariant'],
  watch: {
    drawer: function (newVal, oldVal) {
      // console.log(this.drawerValue)
      this.drawerValue = newVal
      // console.log(this.drawerValue)
    },
  },
  data() {
    return {
      drawerValue: this.drawer,
      items: [
        {
          icon: 'mdi-home-outline',
          title: 'Dashboard',
          to: '/',
        },
        {
          icon: 'mdi-note-text-outline',
          title: 'Manage Post',
          to: '/post',
        },
        {
          icon: 'mdi-comment-question-outline',
          title: 'Manage Question',
          to: '/question',
        },
        {
          icon: 'mdi-book-edit-outline',
          title: 'Manage Write up',
          to: '/write-up',
        },
        {
          icon: 'mdi-account-outline',
          title: 'Manage User',
          to: '/user',
        },
        {
          icon: 'mdi-newspaper-variant-outline',
          title: 'Banner',
          to: '/banner',
        },
      ],
    }
  },
  methods: {
    input(val) {
      this.$emit('close', val)
    },
  },
}
</script>

<style></style>
