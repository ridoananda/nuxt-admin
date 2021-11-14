<template>
  <v-app white>
    <navbar></navbar>

    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <!-- <v-footer app fixed>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer> -->
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      openProfile: false,
      openNotif: false,
      openMail: false,
      selectedItemNotif: null,
      selectedItem: null,
      itemsIcon: [
        { text: 'My profile', icon: 'mdi-account' },
        { text: 'Logout', icon: 'mdi-logout' },
      ],
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
      recent: [
        {
          active: true,
          avatar: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
          title:
            'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae soluta corporis maxime impedit praesentium, cupiditate eveniet quod laudantium iure quidem, reprehenderit consequuntur eaque modi eum nesciunt iusto consectetur perspiciatis non quam exercitationem eos est natus. Molestias, fugiat ea similique officiis inventore numquam veniam impedit aliquam id quia reprehenderit aperiam voluptatem ipsa eius ex officia soluta incidunt possimus porro quis sint. Vero, repellat. Quos blanditiis quam provident nulla animi molestias non dolor consequatur, nesciunt aperiam? Cupiditate, autem, nesciunt officia alias cum excepturi esse iste veniam aut et pariatur porro. Obcaecati culpa consequuntur impedit illo voluptate aliquam magnam nemo omnis consectetur quae?',
        },
        {
          active: true,
          avatar: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
          title: 'Mike Carlson',
        },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/3.jpg',
          title: 'Cindy Baker',
        },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/4.jpg',
          title: 'Ali Connors',
        },
      ],
      previous: [
        {
          title: 'Travis Howard',
          avatar: 'https://cdn.vuetifyjs.com/images/lists/5.jpg',
        },
      ],
      selected: [2],
      itemsMail: [
        {
          action: '15 min',
          headline: 'Brunch this weekend?',
          subtitle: `I'll be in your neighborhood doing errands this weekend. Do you want to hang out?`,
          title: 'Ali Connors',
        },
        {
          action: '2 hr',
          headline: 'Summer BBQ',
          subtitle: `Wish I could come, but I'm out of town this weekend.`,
          title: 'me, Scrott, Jennifer',
        },
        {
          action: '6 hr',
          headline: 'Oui oui',
          subtitle: 'Do you have Paris recommendations? Have you ever been?',
          title: 'Sandra Adams',
        },
        {
          action: '12 hr',
          headline: 'Birthday gift',
          subtitle:
            'Have any ideas about what we should get Heidi for her birthday?',
          title: 'Trevor Hansen',
        },
        {
          action: '18hr',
          headline: 'Recipe to try',
          subtitle:
            'We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
          title: 'Britta Holt',
        },
      ],
      miniVariant: false,
      title: 'Admin',
    }
  },
}
</script>
