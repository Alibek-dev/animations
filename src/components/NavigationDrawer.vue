<template>
  <v-navigation-drawer
      v-model="drawer"
      app
      color="blue-grey lighten-5"
      clipped
  >
    <v-list
        nav
        dense
    >
      <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
      >
        <v-list-item v-for="item of navItems" :key="item.title" link :to="item.link">
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>

      </v-list-item-group>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  name: "NavigationDrawer",
  props: ["drawer"],
  data: () => ({
    group: null,
  }),

  computed: {
    navItems() {
      return [
        { title: "Главная", link: "/" },
        { title: "Матрица", link: "/matrix" }
      ]
    }
  }
}
</script>

<style scoped>

</style>