<template>
  <v-app>
    <v-main>
      <questionnaire />
    </v-main>
  </v-app>
</template>

<script>
import Questionnaire from './pages/Questionnaire.vue';

export default {
  name: 'App',

  components: {
    Questionnaire,
  },

  data: () => ({
    //
  }),
};
</script>
