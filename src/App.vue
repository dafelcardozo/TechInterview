<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" temporary app>
      <v-list  nav>
          <v-list-item link title="Home" :to="{name: 'Home'}" value="home">Home</v-list-item>
          <v-list-item link title="Data" :to="{name: 'Data'}" value="data">Data</v-list-item>
          <v-list-item link title="About" :to="{name: 'About'}" value="about">About</v-list-item>
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
          <v-btn :to="{name: 'Home'}" variant="text" color="primary">Home</v-btn>
          <v-btn :to="{name: 'Data'}" variant="text" color="primary">Data</v-btn>
          <v-btn :to="{name: 'About'}" variant="text" color="primary">About</v-btn>
      </v-app-bar>
    <v-main>
      <v-container>
      <router-view />
      </v-container>
    </v-main>
 </v-app>
 
</template>

<script>
export default {
  name: "App",
  data: () => ({
      drawer: false,
      group: null,
      items: [
        {
          title: 'Foo',
          value: 'foo',
        },
        {
          title: 'Bar',
          value: 'bar',
        },
        {
          title: 'Fizz',
          value: 'fizz',
        },
        {
          title: 'Buzz',
          value: 'buzz',
        },
      ],
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
  
};
</script>
