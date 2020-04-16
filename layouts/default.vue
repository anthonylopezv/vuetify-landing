<template>
  <v-app>
    <Navigation />
    <v-content>
      <nuxt />
    </v-content>
    <Footer />
  </v-app>
</template>

<script>
import Navigation from '../components/Navigation'
import Footer from '../components/Footer'
export default {
  components: {
    Navigation,
    Footer
  }
}
</script>
