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
        { label: "Dashboard", url: "/dashboard" }
      ]
    };
  }
};
</script>