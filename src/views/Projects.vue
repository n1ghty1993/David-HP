<template>
  <span>
    <ProjectHeader></ProjectHeader>
    <v-container fluid>
      <v-row dense>
        <v-col v-for="card in cards" :key="card.title" :cols="card.flex">
          <v-card raised :to="card.url">
            <v-card-title
              v-text="card.title"
              class="justify-center"
            ></v-card-title>
            <v-card-subtitle
              v-text="card.date"
              class="text-center"
            ></v-card-subtitle>
            <v-card-subtitle
              v-text="card.language"
              class="text-center"
            ></v-card-subtitle>
            <v-card-actions>
              <v-btn rounded block color="green darken-2">Zum Projekt</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </span>
</template>

<script>
import ProjectHeader from "@/components/ProjectHeader";
export default {
  name: "Projects",
  components: {
    ProjectHeader
  },
  data: () => ({
    cards: [
      {
        title: "SAE1",
        date: "27 April 2020",
        language: "PHP",
        flex: 3,
        url: "/projects/sae1"
      },
      {
        title: "SAE2",
        date: "27 April 2020",
        language: "SQL",
        flex: 3,
        url: "/projects/sae1"
      }
    ]
  })
};
</script>

<style scoped></style>
