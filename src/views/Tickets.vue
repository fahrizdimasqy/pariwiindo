<template>
  <v-container>
    <v-subheader>
      All Books
    </v-subheader>
    <v-row no-gutters>
      <template v-for="ticket in tickets">
        <v-col :key="ticket.id">
          <v-card class="pa-2 mr-1 ml-1" outlined tile width="183">
            <v-img
              :src="'http://pariwiindo-api.test/images/tickets/' + ticket.image"
              height="125"
              width="160"
              class="grey darken-4"
            ></v-img>

            <v-card-title class="d-block text-truncate">{{
              ticket.title
            }}</v-card-title>
            <v-card-subtitle class="text-truncate">
              {{ ticket.description }}
            </v-card-subtitle>
          </v-card>
        </v-col>
      </template>
    </v-row>
  </v-container>
</template>
<script>
export default {
  name: "Tickets",
  data: () => ({
    tickets: [],
    page: 0,
    lengthPage: 0,
  }),
  created() {
    this.go();
  },
  methods: {
    go() {
      let url = "http://pariwiindo-api.test/v1/tickets?page =" + this.page;
      this.axios
        .get(url)
        .then((response) => {
          let { data } = response.data;
          let { meta } = response.data;
          this.tickets = data;
          this.lengthPage = meta.last_page;
          this.page = meta.current_page;
        })
        .catch((error) => {
          let { responses } = error;
          console.log(responses);
        });
    },
  },
};
</script>
