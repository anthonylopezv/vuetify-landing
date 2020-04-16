<template>
  <v-card width="368" height="480" class="mx-auto my-10 px-6 py-6">
    <v-card-title>
      <h1 class="display-1 my-0 mx-auto heading">Iniciar sesión</h1>
    </v-card-title>
    <v-card-text class="mt-6">
      <v-form>
        <v-text-field 
          label="Correo"
          prepend-icon="mdi-account-circle"
        />
        <v-text-field
          :type="showPassword ? 'text' : 'password'" 
          label="Contraseña"
          prepend-icon="mdi-lock"
          :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="showPassword = !showPassword"
        />
      </v-form>
    </v-card-text>
    <div class="px-4 pt-0">
      <v-btn color="info" width="288">Ingresar</v-btn>
      <v-btn color="success" width="288" outlined class="mt-4">Registrarse</v-btn>
      <hr class="my-7 gradient">
      <p class="text-center">¿Olvidaste tu contraseña?
        <a class="link" href="">Recupérala</a>
      </p>
    </div>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      showPassword: false
    }
  }
}
</script>

<style>
  .heading {
    font-weight: 500 !important;
  }
  .gradient {
    border: 0;
    height: 1px;
    background-image: linear-gradient(to right, white 0%, #d9d9d9 50%, white 100%);
  }
  .link {
    font-weight: 700;
    text-decoration: none;
    color: #2196f3 !important;
  }
</style>
