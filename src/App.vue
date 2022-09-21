<template>
  <v-app>
    <v-app-bar
        app
        color="primary"
        dark
    >
      <div class="d-flex align-center">
        <v-img
            alt="Vuetify Logo"
            class="shrink mr-2"
            contain
            src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
            transition="scale-transition"
            width="40"
        />

        <v-img
            alt="Vuetify Name"
            class="shrink mt-1 hidden-sm-and-down"
            contain
            min-width="100"
            src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
            width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
          href="https://github.com/dllpl"
          target="_blank"
          text
      >
        <span class="mr-2">Автор @dllpl</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-row class="mt-6" justify="center" cols="12">
          <v-col md="6" sm="12">
            <div class="mb-3">Компонент для работы с Dadata.ru</div>
            <DadataHints/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>

import DadataHints from "./components/DadataHints";

export default {
  name: 'App',

  components: {
    DadataHints
  },

  data: () => ({
    //
  }),
};
</script>
