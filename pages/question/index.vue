<template>
  <v-card>
    <v-card-title>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="desserts"
      :items-per-page="5"
      :search="search"
      class="elevation-1"
    ></v-data-table>
  </v-card>
</template>

<script>
export default {}
</script>

<style></style>
