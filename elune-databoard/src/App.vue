<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Elune</span>
        <span class="font-weight-light">Data Dashboard</span>
      </v-toolbar-title>
    </v-app-bar>

    <v-content>
      <DataForm/>
    </v-content>
  </v-app>
</template>

<script>
import DataForm from './components/DataForm';

export default {
  name: 'App',
  components: {
    DataForm
  },
  data: () => ({
    //
  }),
};
</script>
