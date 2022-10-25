<template>
  <v-combobox
      v-model="searchText"
      @keyup="send($event.target.value)"
      :label="label"
      :items="items"
      item-text="value"
      clearable
      outlined
  ></v-combobox>
</template>

<script>
import axios from 'axios'

export default {
  name: "DadataHints",
  props: {
    type: {type: String, default: 'address'},
    label: {type: String, default: 'Адрес'},
    count: {type: Number, default: 10},
    token: {type: String}
  },
  data() {
    return {
      searchText: '',
      items: [],
      config: {}
    }
  },
  methods: {
    send(val) {
      let payload = {
        query: val,
        count: this.count
      }
      axios.post(`https://suggestions.dadata.ru/suggestions/api/4_1/rs/suggest/${this.type}`, payload, this.config)
          .then(({data}) => {
            this.items = data.suggestions
          })
    },
  },
  mounted() {
    this.config = {
      headers: {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Token " + process.env.VUE_APP_DADATA_PUBLIC_TOKEN
      }
    }
  },
  watch: {
    searchText: function (val) {
      this.$emit('setDataJson', val)
    }
  }
}
</script>

<style scoped>

</style>