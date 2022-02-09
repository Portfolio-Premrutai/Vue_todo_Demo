<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />
<router-link to="/">
        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        /></router-link>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        @click="$router.push('/about')"
        target="_blank"
        text
      >
        <span class="mr-2">About Us</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>
      <!-- <v-content>
       
      <HelloWorld/>
        <Home/>
        <About/> 
      </v-content> -->
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue"
import Home from "./views/Home.vue"
import About from "./views/About.vue"
export default {
  name: "App",

  component:{
    // HelloWorld,
    Home,
    About
  },
  // data: () => ({
  //   //
  // }),
};
</script>
