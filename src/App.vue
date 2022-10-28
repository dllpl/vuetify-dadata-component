<template>
  <v-app>
    <Header/>
    <v-main>
      <v-container>
        <v-row class="mt-6" justify="center" cols="12">
          <v-col md="6" sm="12">
            <v-card>
              <v-card-title class="font-weight-bold">Компонент Vuetify для работы с сервисом подсказок</v-card-title>
              <v-card-subtitle><a href="https://dadata.ru" target="_blank">Dadata.ru</a></v-card-subtitle>
              <v-card-text>
                <v-divider class="mb-3"></v-divider>
                <div>Вариант поиска:</div>
                <v-radio-group
                    v-model="type"
                    row
                >
                  <v-radio v-for="option in searchOptions"
                           :key="option.id"
                           :label=option.label
                           :value=option.type
                           v-model="option.type"
                  ></v-radio>
                </v-radio-group>
                <div>Количество выводимых подсказок:</div>
                <v-slider
                    v-model="count"
                    thumb-label
                    max="20"
                >
                  <template v-slot:append>
                    <v-text-field
                        v-model="count"
                        class="mt-0 pt-0"
                        hide-details
                        single-line
                        type="number"
                        style="width: 60px"
                    ></v-text-field>
                  </template>
                </v-slider>
                <DadataHints
                    :type="type"
                    :label="label"
                    :count="count"
                    @setDataJson="setDataJson"
                />
              </v-card-text>
            </v-card>
            <DadataView :json="json"/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>

import Header from "./components/Header"
import DadataHints from "./components/DadataHints"
import DadataView from "./components/DadataView"

export default {
  name: 'App',
  components: {DadataView, Header, DadataHints},
  data() {
    return {
      searchOptions: [
        {
          label: 'Адрес',
          type: 'address',
        },
        {
          label: 'ФИО',
          type: 'fio',
        },
        {
          label: 'Организация',
          type: 'party',
        },
        {
          label: 'Банк',
          type: 'bank',
        },
        {
          label: 'Email',
          type: 'email',
        },
      ],
      type: 'address',
      label: 'Адрес',
      count: 10,
      json: '',
    }
  },
  watch: {
    type(type) {
      switch (type) {
        case 'address':
          this.label = 'Адрес'
          break
        case 'fio':
          this.label = 'ФИО'
          break
        case 'party':
          this.label = 'Организация'
          break
        case 'bank':
          this.label = 'Банк'
          break
        case 'email':
          this.label = 'Email'
          break
      }
    }
  },
  methods: {
    setDataJson(json) {
      console.log(json)
      json ? this.json = JSON.stringify(json, null, '\t') : this.json = json
    },
  }
};
</script>
