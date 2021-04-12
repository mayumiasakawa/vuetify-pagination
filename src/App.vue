<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title>
        <span>Vuetify Pagination</span>
      </v-toolbar-title>
    </v-app-bar>
    <v-content>
      <div class="text-center">
        <v-pagination
        v-model="page"
        :length="6"
        >
        </v-pagination>
      </div>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      page: 1,
    }
  }
};
</script>
