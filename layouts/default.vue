<template>
  <v-app >
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-tile
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title" />
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-toolbar-side-icon @click="drawer = !drawer" />
     
    </v-toolbar>
    
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
   
    <v-footer
    dark
    height="auto"
  >
    <v-card
      flat
      tile
      class=" text-xs-center"
      color='#f5f5f5'
    >
     <br>
     <br>
      <v-card-text class="white--text pt-0 black-text">
        It is essential to stay relevant in this world, the Internet is another world we live in today, 
        go LIVE! with an outstanding web platform today!  <router-link to='/contact' class=' badge'> Contact Me</router-link>
        . I am professionally inclined to create your needed website in view of achieving the desired goals.
      </v-card-text>
  <share></share>
      <v-divider></v-divider>

      <v-card-text class="white--text black-text">
        &copy;2019 — <strong>MobyTech</strong>
      </v-card-text>
    </v-card>
  </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'bubble_chart',
          title: 'services',
          to: '/services'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
