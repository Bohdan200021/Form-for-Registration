<template>
  <v-app>
    <RegistrationForm />
  </v-app>
</template>

<script>
import RegistrationForm from './components/RegistrationForm.vue';


export default {
  name: 'App',

  components: {
    RegistrationForm,
  },

  data: () => ({
    //
  }),
};
</script>
style