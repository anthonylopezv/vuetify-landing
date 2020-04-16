<template>
  <v-footer
    color="primary"
    padless
  >
    <v-row
      justify="center"
      no-gutters
    >
      <nuxt-link
        v-for="link in links"
        :key="link.name"
        :to="link.route"
      >
        <v-btn
          color="white"
          text
          rounded
          class="my-2"
        >
          {{ link.name }}
        </v-btn>
      </nuxt-link>
      <v-col
        class="primary lighten-2 py-4 text-center white--text"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Vuetify Dashboard</strong>
      </v-col>
    </v-row>
  </v-footer>
</template>

<script>
export default {
  name: 'Footer',

  data() {
    return {
      links: [
        // {name: 'Inicio', route: '/'},
        // {name: 'Login', route: '/login'}
      ]    
    }
  },
}
</script>