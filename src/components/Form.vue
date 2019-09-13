<template>
<div>
  <v-container>

  <v-form>
    <v-jsonschema-form v-if="schema" :schema="schema" :model="dataObject" :options="options" @error="showError" @change="showChange" @input="showInput" />
  </v-form>
  <v-flex>
    <v-btn @click="view">
      Mostrar payload
    </v-btn>
  </v-flex>
  </v-container>
</div>
</template>

<script>
import VJsonschemaForm from '@koumoul/vuetify-jsonschema-form/lib/index.vue'
import {mask} from 'vue-the-mask'

export default {
  directives: {
    mask
  },	
  components: {
    VJsonschemaForm
  },
  data: () => ({
    schema: {
      title: "Product",
      description: "A product from Acme's catalog",
      type: "object",
      properties: {
        productId: {
          description: "The unique identifier for a product",
          type: "integer"
        },
        homepage: {
          description: 'A long string also, but display is forced on single line',
          type: 'string',
          maxLength: 2000,
          'x-display': 'single-line'
        },
        nome: {
          description: "The unique identifier for a name",
          type: "string"
        },
        fromEnum: {
          title: "From enum",
          type: "string",
          description: "The values are simple strings coming from an enum.",
          enum: [
            "value1",
            "value2",
            "value3"
          ]
        },
        aDate: {
          title: "A date",
          type: "string",
          format: "date",
        },
        password: {
          type: "string",
          "x-display": "password",
        },
        ageSlider: {
          description: "Same age, but in a slider.",
          type: "integer",
          'x-display': "slider",
          minimum: 0,
          maximum: 150
        },
        citizen: {
          description: "Is this person a citizen of this country.",
          type: "boolean"
        },
        aTime: {
          title: "A time",
          type: "string",
          format: "time",
          description: "A time."
        },
      },
      required: [ "productId" ],
    },
    dataObject: {},
    formValid: false,
    options: {
      debug: false,
      disableAll: false,
      autoFoldObjects: true
    }
  }),
   methods: {
    showError(err) {
      window.alert(err)
    },
    showChange(e) {
      console.log('"change" event', e)
    },
    showInput(e) {
      console.log('"input" event', e)
    },
    view() {
      alert(JSON.stringify(this.dataObject))
    }
  }
}

</script>
<style>

</style>