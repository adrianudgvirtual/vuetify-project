<template>
    <v-navigation-drawer expand-on-hover permanent >
      <v-list>
        <v-list-item prepend-avatar="#" title="Adrian Cortes"
          subtitle="En Línea"></v-list-item>
      </v-list>
      <v-divider></v-divider>
      <v-list density="compact" nav>
        <v-list-item v-for="item in items" :key="item.title" router :to="item.route" :prepend-icon="item.icon"
          :title="item.title" :value="item.title"></v-list-item>
      </v-list>
    </v-navigation-drawer>
  </template>
  
  <script>
  export default {
    data() {
      return {
        drawer: true,
        items: [
          { icon: 'mdi-speedometer', title: 'Inicio', route: '/' },
          { icon: 'mdi-film', title: 'Rick And Morty', route: '/rickandmorty' }
        ],
      }
    }
  }
  </script>