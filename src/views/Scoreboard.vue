<template>
  <v-container>
    <v-layout
        text-center
        wrap
    >
      <v-flex
          xs12
      >
        <v-card>
          <v-card-title>
            Scoreboard
            <v-spacer></v-spacer>
            <v-text-field
                v-model="search"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
            ></v-text-field>
          </v-card-title>
          <v-data-table
              :headers="headers"
              :items="items"
              :search="search"
          ></v-data-table>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
export default {
  data: () => ({
    search: "",
    headers: [
      {
        text: 'Name',
        align: 'center',
        value: 'Name',
      },
      {
        text: 'Count',
        align: 'center',
        value: 'Count',
      },
    ],
    items: [],
  }),
  mounted() {
    this.getAllAffectedApp()
  },
  methods: {
    getAllAffectedApp: function () {
      this.$http.get(process.env.VUE_APP_ALICE +"/read/") //NANTI GANTI SESUAI DOMAIN
          .then(response => {
            this.items = response.data.data
          })
          .catch(e => {
            console.log(e)
          })
    },
  }
};
</script>