<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Registro</h1>
        <v-form ref="signUpForm" v-model="formValidity">
          <v-text-field 
            type="email" 
            label="Correo"
            v-model="email"
            :rules="emailRules"
            required
          ></v-text-field>
          <v-autocomplete 
            label="¿Cuál es su navegador de preferencia?"
            :items="browsers"
          ></v-autocomplete>
          <v-file-input label="Agregar foto de perfil"></v-file-input>
          <v-text-field
            label="Fecha de nacimiento"
            v-model="birthday"
            readonly
          ></v-text-field>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-checkbox 
            label="Agregar términos y condiciones" 
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
            required
          ></v-checkbox>
          <v-btn type="submit" color="primary" :disabled="!formValidity">Registrarse</v-btn>
          <v-btn color="warning" @click="resetValidation">Reiniciar validacion</v-btn>
          <!-- <v-btn color="error" @click="resetForm">Reiniciar</v-btn> -->
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      agreeToTerms: false,
      agreeToTermsRules: [
        value =>
          !!value ||
          'You must agree to the terms and conditions to sign up for an account.'
      ],
      birthday: '',
      browsers: ['Chrome', 'Firefox', 'Safari', 'Edge', 'Brave'],
      email: '',
      emailRules: [
        value => !!value || 'Email is required.',
        value => value.indexOf('@') !== 0 || 'Email should have a username.',
        value => value.includes('@') || 'Email should include an @ symbol.',
        value =>
          value.indexOf('.') - value.indexOf('@') > 1 ||
          'Email should contain a valid domain.',
        value => value.includes('.') || 'Email should include a period symbol.',
        value =>
          value.indexOf('.') <= value.length - 3 ||
          'Email should contain a valid domain extension.'
      ],
      formValidity: false
    }
  },
  methods: {
    // resetForm() {
    //   this.$refs.signUpForm.reset()
    // },
    resetValidation() {
      this.$refs.signUpForm.resetValidation()
    },
    validateForm() {
      this.$refs.signUpForm.validate()
    }
  }
}
</script>