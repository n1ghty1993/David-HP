<template>
  <span>
    <v-navigation-drawer
      app
      v-model="drawer"
      class="green darken-2"
      dark
      disable-resize-watcher
    >
      <v-list>
        <template v-for="(item, index) in items">
          <v-list-item :key="index">
            <v-list-item-content>
              <router-link :to="{ path: item.route }">{{
                item.title
              }}</router-link>
            </v-list-item-content>
          </v-list-item>
          <v-divider :key="`divider-${index}`"></v-divider>
        </template>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app color="green darken-2" dark>
      <v-app-bar-nav-icon
        class="hidden-md-and-up"
        @click="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <router-link to="/"
        ><v-toolbar-title class="mr-1">{{
          appTitle
        }}</v-toolbar-title></router-link
      >
      <v-btn text class="hidden-sm-and-down" to="/projects">Projekte</v-btn>
      <v-spacer class="hidden-sm-and-down"></v-spacer>
      <v-btn text class="hidden-sm-and-down">Login</v-btn>
    </v-app-bar>
  </span>
</template>

<script>
export default {
  name: "Navigation",
  data() {
    return {
      appTitle: "David Louis",
      drawer: false,
      items: [{ title: "Projekte", route: "/p" }, { title: "Login" }]
    };
  }
};
</script>

<style scoped>
.v-application a {
  color: white;
  text-decoration: none;
}
</style>
