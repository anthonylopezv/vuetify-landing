<template>
  <v-app-bar app color="primary" dark>
    <v-toolbar-title>Vuetify Dashboard</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn 
      v-for="link in links" 
      :key="link.label" 
      :to="link.url" 
      text 
      rounde
    >
      {{ link.label }}
    </v-btn>
    <v-btn @click="toggleTheme" text rounded>
      Tema
    </v-btn>      
  </v-app-bar>
</template>

<script>
export default {
  name: "Navigation",

  data() {
    return {
      links: [
        { label: "Inicio", url: "/" },
        { label: "Login", url: "/login" },
        { label: 'Registro', url: '/signup' },
        { label: "Dashboard", url: "/dashboard" }
      ]
    };
  },
  methods: {
    toggleTheme() {
      this.$vuetify.theme.themes.dark.archor = '#8c9eff'
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
    }
  }
}
</script>