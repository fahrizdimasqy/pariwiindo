<template>
  <v-app>
    <v-app-bar app color="white" light>
      <v-app-bar-nav-icon class="mt-5" @click.stop="drawer = !drawer">
      </v-app-bar-nav-icon>
      <v-spacer></v-spacer>
      <v-img
        src="https://i.pinimg.com/564x/f6/ec/c6/f6ecc60cefe2f549fa92714571b8bbc1.jpg"
        class="user-image mt-5"
        max-width="30"
      />
    </v-app-bar>
    <v-navigation-drawer app v-model="drawer">
      <div class="pa-2" v-if="guest">
        <v-btn block color="primary" class="mb-2">
          <v-icon left>mdi-lock</v-icon>
          Login
        </v-btn>
        <v-btn block color="success">
          <v-icon left>mdi-account</v-icon>
          Register
        </v-btn>
      </div>
      <v-list>
        <v-list-item v-if="!guest">
          <v-list-item-avatar>
            <v-img
              src="https://i.pinimg.com/564x/f6/ec/c6/f6ecc60cefe2f549fa92714571b8bbc1.jpg"
            ></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>Angel</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>
        <v-list-item
          v-for="(item, index) in menus"
          :key="`menu-` + index"
          :to="item.route"
        >
          <v-list-item-icon>
            <v-icon left>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <template v-slot:append v-if="!guest">
        <div class="pa-2">
          <v-btn block color="red" dark>
            <v-icon left>mdi-lock</v-icon>
            Logout
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>

    <v-main>
      <!-- <Home /> -->
      <router-view></router-view>
    </v-main>
    <v-bottom-navigation fixed :value="value" color="primary">
      <v-btn>
        <span>Home</span>
        <v-icon>mdi-home</v-icon>
      </v-btn>

      <v-btn>
        <span>Cart</span>
        <v-icon>mdi-cart</v-icon>
      </v-btn>

      <v-btn>
        <span>List</span>
        <v-icon>mdi-format-list-bulleted</v-icon>
      </v-btn>

      <v-btn>
        <span>Profile</span>

        <v-icon>mdi-face</v-icon>
      </v-btn>
    </v-bottom-navigation>
  </v-app>
</template>

<script>
// import Home from "./views/Home";
// import TicketCard from "./components/TicketCard";
// optional style for arrows & dots
// import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";
// import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";
export default {
  name: "App",

  components: {
    // VueSlickCarousel,
    // TicketCard
    // Home,
  },

  data: () => ({
    //
    drawer: false,
    menus: [
      { title: "Home", icon: "mdi-home", route: "/" },
      { title: "About", icon: "mdi-account", route: "/about" }
    ],
    guest: false,
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
            slidesToShow: 1
          }
        },
        {
          breakpoint: 600,
          settings: {
            arrow: false,
            swipe: true,
            swipeToSlide: true,
            slidesToShow: 1
          }
        },
        {
          breakpoint: 480,
          settings: {
            swipe: true,
            swipeToSlide: true,
            arrow: false,
            slidesToShow: 1
          }
        }
      ]
    },
    value: 0,
    computed: {
      isHome() {
        return this.$route.path === "/";
      }
    }
  })
};
</script>
<style scoped>
.v-sheet.v-toolbar:not(.v-sheet--outlined) {
  box-shadow: none !important;
}
.user-image {
  /* margin-top: 10%; */
  border-radius: 10px;
}
</style>
