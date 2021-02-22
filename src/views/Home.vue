<template>
  <div>
    <v-container>
      <h1>Hi Angel,</h1>
      <p class="text--disabled">Buy your ticket</p>

      <div class="text-right">
        <v-btn small text to="/categories" class="blue--text">
          All Promos <v-icon>mdi-chevron-right</v-icon>
        </v-btn>
      </div>

      <v-row dense>
        <v-col cols="12">
          <v-card color="#2196F3" dark max-height="90">
            <v-card-title class="headline">
              Promo
            </v-card-title>

            <v-card-subtitle>Extra Promo Hingga 50%</v-card-subtitle>

            <v-card-actions>
              <v-btn text>
                Listen Now
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <promo-ticket />
  </div>
</template>

<script>
// @ is an alias to /src
import PromoTicket from "../components/PromoTicket";
// import TicketCard from "../components/TicketCard";
// import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";
export default {
  name: "Home",
  components: {
    // VueSlickCarousel,
    "promo-ticket": PromoTicket,
    // TicketCard,
  },
  data: () => ({
    carousel: {
      arrow: true,
      infinite: false,
      focusOnSelect: true,
      variableWidth: true,
      speed: 500,
      slidesToShow: 1,
      swipe: false,
      initialSlide: 0,
      responsive: [
        {
          breakpoint: 1024,
          settings: {
            arrow: false,
            slidesToShow: 1,
          },
        },
        {
          breakpoint: 600,
          settings: {
            arrow: false,
            swipe: true,
            swipeToSlide: true,
            slidesToShow: 1,
          },
        },
        {
          breakpoint: 480,
          settings: {
            swipe: true,
            swipeToSlide: true,
            arrow: false,
            slidesToShow: 1,
          },
        },
      ],
    },
    settings: {
      dots: true,
      dotsClass: "slick-dots custom-dot-class",
      edgeFriction: 0.35,
      infinite: false,
      speed: 500,
      slidesToShow: 1,
      slidesToScroll: 1,
    },
    promo: [
      {
        id: 1,
        image: "https://via.placeholder.com/150",
        name: "Ekonomi",
        slug: "ekonomi",
        price: 15000,
      },
      {
        id: 1,
        image: "https://via.placeholder.com/150",
        name: "Ekonomi",
        slug: "ekonomi",
        price: 20000,
      },
    ],
  }),
};
</script>
