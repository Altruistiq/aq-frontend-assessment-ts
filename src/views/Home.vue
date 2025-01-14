<template>
  <main>
    <h1>Altruistiq frontend tech assessment</h1>
    <p>Please check the console for initial API logs</p>
  </main>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'
  import { mapStores } from 'pinia'

  import { useDataStore } from '@/stores/dataStore'

  export default defineComponent({
    name: 'home',

    computed: {
      ...mapStores(useDataStore),
    },

    mounted() {
      this.getData()
    },

    methods: {
      async getData() {
        try {
          // get all countries
          const countries = await this.dataStore.getCountries()

          // get data for a single country
          const data = await this.dataStore.getCountry(229)

          console.log('countries', countries)
          console.log('data for single country (UK)', data)
        } catch (err) {
          console.error(err)
        }
      },
    },
  })
</script>
