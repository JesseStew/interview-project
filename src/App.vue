<template>
  <v-app>
    <v-navigation-drawer
      app
      fixed
      temporary
      v-model="drawer"

    >
      <v-list>
        <v-list-item :to="page.path" link v-for="page in pages" :key="page.id">
          <v-list-item-icon>
            <v-icon> {{page.icon}} </v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>
              {{page.name}}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-spacer></v-spacer>
      <span class="h3">
        Title
      </span>
      <v-spacer></v-spacer>
      <template v-slot:extension>
        <v-tabs
          centered
          center-active
        >
          <v-tab router :to="page.path" v-for="page in pages" :key="page.id">
            {{ page.name }}
          </v-tab>
        </v-tabs>
      </template>
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-main>

    <v-footer app>
      <!--  -->
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  components: {
  },

  data() {
    return {
      drawer: false,
      pages: [
        {
          id: 0,
          path: '/',
          name: 'Home',
          icon: 'mdi-home',
        },
        {
          id: 1,
          path: '/about',
          name: 'About',
          icon: 'mdi-account',
        },
        {
          id: 2,
          path: '/contact',
          name: 'Contact',
          icon: 'mdi-phone',
        },
        {
          id: 3,
          path: '/team',
          name: 'Team',
          icon: 'mdi-account-group',
        },
        {
          id: 4,
          path: '/treatments',
          name: 'Treatments',
          icon: 'mdi-hand-heart',
        },
        {
          id: 5,
          path: '/blog',
          name: 'Blog',
          icon: 'mdi-post',
        },
      ]
    }
  },
};
</script>
