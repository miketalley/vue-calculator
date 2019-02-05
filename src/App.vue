<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Vue Calculator</span>
      </v-toolbar-title>
    </v-toolbar>

    <v-content>
      <Calculator/>
    </v-content>
  </v-app>
</template>

<script>
import Calculator from './components/Calculator.vue';

export default {
  name: 'App',
  components: {
    Calculator,
  },
};
</script>
