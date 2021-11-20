<template>
  <div>
    <v-app-bar fixed app elevate-on-scroll>
      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        v-show="!$vuetify.breakpoint.mdAndUp"
      />
      <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
        v-show="$vuetify.breakpoint.mdAndUp"
      >
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-row>
        <v-col class="d-flex justify-end align-center">
          <v-menu
            v-model="openMail"
            :close-on-content-click="true"
            bottom
            right
            rounded="lg"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-badge
                top
                color="purple accent-4"
                dot
                offset-x="10"
                offset-y="10"
                class="mr-5 mr-md-8"
              >
                <v-icon v-on="on" v-bind="attrs" size="25">
                  mdi-email-outline
                </v-icon>
              </v-badge>
            </template>
            <v-list two-line subheader>
              <v-list-item-group v-model="selected" active-class="pink--text">
                <template v-for="(item, index) in itemsMail">
                  <v-list-item :key="item.title">
                    <template>
                      <v-list-item-content>
                        <v-list-item-title
                          v-text="item.title"
                        ></v-list-item-title>
                        <v-list-item-subtitle
                          class="text--primary"
                          v-text="item.headline"
                        ></v-list-item-subtitle>
                        <v-list-item-subtitle
                          v-text="item.subtitle"
                        ></v-list-item-subtitle>
                      </v-list-item-content>
                      <v-list-item-action>
                        <v-list-item-action-text
                          v-text="item.action"
                        ></v-list-item-action-text>
                      </v-list-item-action>
                    </template>
                  </v-list-item>
                  <v-divider
                    v-if="index < items.length - 1"
                    :key="index"
                  ></v-divider>
                </template>
              </v-list-item-group>
            </v-list>
          </v-menu>
          <v-menu
            v-model="openNotif"
            :close-on-content-click="true"
            bottom
            right
            rounded="lg"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-badge
                top
                color="deep-purple accent-4"
                dot
                offset-x="10"
                offset-y="10"
                class="mr-5 mr-md-8"
              >
                <v-icon v-on="on" v-bind="attrs" size="25">
                  mdi-bell-outline
                </v-icon>
              </v-badge>
            </template>
            <v-list subheader dense>
              <v-subheader class="d-flex justify-space-between">
                <div>Notification</div>
                <v-icon
                  @click="openNotif = false"
                  class="font-weight-bold cursor-pointer"
                >
                  mdi-close
                </v-icon>
              </v-subheader>
              <v-list-item-group v-model="selectedItemNotif" color="primary">
                <v-list-item link v-for="chat in recent" :key="chat.title">
                  <v-list-item-icon class="mr-4">
                    <v-icon>
                      mdi-bell-outline
                    </v-icon>
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title
                      @click="$router.push('/')"
                      class="cursor-pointer"
                    >
                      {{ chat.title }}
                    </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-item-group>
            </v-list>
          </v-menu>
          <v-menu
            rounded="lg"
            :close-on-click="true"
            bottom
            right
            v-model="openProfile"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-avatar size="40" v-on="on" v-bind="attrs">
                <img
                  alt="Avatar"
                  src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
                />
              </v-avatar>
            </template>
            <v-list>
              <v-list-item>
                <v-list-item-avatar>
                  <v-img
                    src="https://cdn.vuetifyjs.com/images/john.png"
                  ></v-img>
                </v-list-item-avatar>
              </v-list-item>
              <v-list-item link>
                <v-list-item-content>
                  <v-list-item-title class="text-h6">
                    John Leider
                  </v-list-item-title>
                  <v-list-item-subtitle>
                    john@vuetifyjs.com
                  </v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-list>
            <v-divider></v-divider>
            <v-list nav dense>
              <v-list-item-group v-model="selectedItem" color="primary">
                <v-list-item v-for="(item, i) in itemsIcon" :key="i">
                  <v-list-item-icon>
                    <v-icon v-text="item.icon"></v-icon>
                  </v-list-item-icon>
                  <v-list-item-content>
                    <v-list-item-title v-text="item.text"></v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-item-group>
            </v-list>
          </v-menu>
        </v-col>
      </v-row>
    </v-app-bar>
    <Sidebar :drawer="drawer" @close="closeDrawer" />
  </div>
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
  methods: {
    closeDrawer(val) {
      this.drawer = val
    },
  },
}
</script>

<style></style>
