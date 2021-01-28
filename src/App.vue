<template>
    <v-app id="app">
        <v-navigation-drawer
        color="green"
        dark
        expand-on-hover
        hide-overlay
        permanent
        right
        app>
        </v-navigation-drawer>

        <v-content class="px-12 py-3">
          <v-container fluid>
            <router-view/>
          </v-container>
        </v-content>

    </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
