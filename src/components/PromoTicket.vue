<template>
  <v-app>
    <v-container fluid>
      <div class="text-right">
        <v-btn small text to="/tickets" class="blue--text">
          All Tickets <v-icon>mdi-chevron-right</v-icon>
        </v-btn>
      </div>
      <h4>Ticket</h4>
      <v-row dense>
        <v-col v-for="ticket in tickets" :key="ticket.id" :cols="ticket.flex">
          <v-card max-height="300">
            <v-img
              :src="'http://pariwiindo-api.test/images/tickets/' + ticket.image"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="150px"
            >
              <v-card-title
                v-text="ticket.title"
                class="title-text"
              ></v-card-title>
            </v-img>

            <v-card-actions>
              <div class="d-inline-block text-truncate">
                <v-card-subtitle class="text-truncate"
                  >{{ ticket.description }}
                </v-card-subtitle>
                <v-card-text>{{ `Rp.${ticket.price}` }}</v-card-text>
              </div>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  name: "PromoTicket",
  data: () => ({
    tickets: []
  }),
  created() {
    console.log("get data categories");
    this.axios
      .get("http://pariwiindo-api.test/v1/tickets")
      .then(response => {
        let { data } = response.data;
        this.tickets = data;
      })
      .catch(error => {
        let { response } = error;
        console.log(response);
      });
  }
};
</script>
<style scoped></style>
