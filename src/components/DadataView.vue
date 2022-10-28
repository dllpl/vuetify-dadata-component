<template>
  <v-card class="mt-6" v-show="json">
    <v-card-title>Ответ сервиса:</v-card-title>
    <v-card-text>
      <pre>{{ json }}</pre>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "DadataView",
  props: {
    json: {
      type: String,
      default: ''
    }
  }
}
</script>
