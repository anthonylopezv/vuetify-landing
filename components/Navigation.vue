<template>
  <v-app-bar app color="primary" dark>
    <v-toolbar-title>Vuetify Dashboard</v-toolbar-title>
    <v-spacer></v-spacer>
    <nuxt-link
      v-for="link in links"
      :key="link.name"
      :to="link.route"
    >
      <v-btn text rounde>{{ link.name }}</v-btn>
    </nuxt-link>
  </v-app-bar>
</template>

<script>
export default {
  name: 'Navigation',

  data() {
    return {
      links: [
        {name: 'Inicio', route: '/'},
        {name: 'Login', route: '/login'}
      ]    
    }
  }
  
}
</script>