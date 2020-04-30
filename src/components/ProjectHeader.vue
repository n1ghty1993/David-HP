<template>
  <v-container fluid fill-height class="Startpage">
    <v-layout justify-center align-center column pa-5>
      <div class="display-3 font-weight-black white--text textcenter">
        PROJECTS
      </div>
      <div class="display-1 font-weight-bold white--text text-center">
        Here you can find all of my projects
      </div>
      <v-btn fab class="mt-5 green darken-3">
        <v-icon large color="white">mdi-chevron-down</v-icon>
      </v-btn>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: "ProjectHeader"
};
</script>

<style scoped>
.Startpage {
  background: url("~@/assets/home-bg.jpg");
  background-size: cover;
  width: 100%;
  height: 100%;
}
</style>
