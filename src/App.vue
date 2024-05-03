<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" temporary app>
      <v-list density="compact" nav>
          <v-list-item prepend-icon="mdi-home" link title="Home" :to="{name: item.name}" :value="{name}" v-for="item of primary_menu" :key="item.name">
            <v-icon :class="'mdi mdi-'+item.icon" end /> <div>{{item.name}}</div>
          </v-list-item>
      </v-list>
      </v-navigation-drawer>
    <v-app-bar app color="primary" dark clipped-left >
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <div class="d-flex align-center">
          <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
        </div>
        <v-spacer></v-spacer>
        <v-btn :to="{name: item.name}" variant="text" color="primary" v-for="item of primary_menu" :key="item.name">
          <v-icon :class="'mdi mdi-'+item.icon" end />
        </v-btn>
      </v-app-bar>
    <v-main>
      <v-container>
      <router-view />
      </v-container>
    </v-main>
 </v-app>
 
</template>

<script>
import '@mdi/font/css/materialdesignicons.css';

export default {
  name: "App",
  data: () => ({
      drawer: false,
      group: null,
      primary_menu: [{name:"Home", icon:"home"}, {name:"Data", icon: "database"}, {name: "About", icon:"help"}],
      secondary_menu:
      {
    ecosystem: [
      {
        text: "vuetify-loader",
        href: "https://github.com/vuetifyjs/vuetify-loader",
      },
      {
        text: "github",
        href: "https://github.com/vuetifyjs/vuetify",
      },
      {
        text: "awesome-vuetify",
        href: "https://github.com/vuetifyjs/awesome-vuetify",
      },
    ],
    importantLinks: [
      {
        text: "Documentation",
        href: "https://vuetifyjs.com",
      },
      {
        text: "Chat",
        href: "https://community.vuetifyjs.com",
      },
      {
        text: "Made with Vuetify",
        href: "https://madewithvuejs.com/vuetify",
      },
      {
        text: "Twitter",
        href: "https://twitter.com/vuetifyjs",
      },
      {
        text: "Articles",
        href: "https://medium.com/vuetify",
      },
    ],
    whatsNext: [
      {
        text: "Explore components",
        href: "https://vuetifyjs.com/components/api-explorer",
      },
      {
        text: "Select a layout",
        href: "https://vuetifyjs.com/getting-started/pre-made-layouts",
      },
      {
        text: "Frequently Asked Questions",
        href: "https://vuetifyjs.com/getting-started/frequently-asked-questions",
      },
    ],
  }
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
  
};
</script>
