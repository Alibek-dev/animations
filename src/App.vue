<template>
  <div>
    <v-app>
      <NavigationDrawer :drawer="drawer" />
      <v-app-bar  clipped-left app color="blue-grey lighten-5">
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"><v-icon>mdi-menu</v-icon></v-app-bar-nav-icon>
      </v-app-bar>
      <v-main app>
        <v-card height="100%" width="100%" class="container">
          <router-view/>
        </v-card>
      </v-main>
    </v-app>
  </div>


</template>

<script>

import NavigationDrawer from "@/components/NavigationDrawer";

export default {
  name: 'App',
  components: { NavigationDrawer },
  data: () => ({
    drawer: true,
  })
}
</script>

<style>
</style>
