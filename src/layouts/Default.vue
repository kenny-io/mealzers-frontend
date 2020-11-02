<template>
  <v-app>
    <div>
      <v-app-bar
        absolute
        color="orange"
        dark
        shrink-on-scroll
        scroll-target="#scrolling-techniques-2"
      >
        <v-app-bar-nav-icon class="mt-5" @click="drawer = !drawer">
        </v-app-bar-nav-icon>
        <g-link
          class="mt-7 ml-3"
          style="text-decoration: none; color: inherit"
          to="/"
          >Mealzers</g-link
        >
        <v-spacer></v-spacer>
        <v-btn outlined rounded dense class="mt-5 mr-3">
          <g-link style="text-decoration: none; color: inherit" to="/shop/"
            >Shop</g-link
          >
        </v-btn>
        <v-btn outlined rounded dense class="mt-5 mr-3">
          <g-link style="text-decoration: none; color: inherit" to="/support/"
            >Support</g-link
          >
        </v-btn>
        <v-text-field
          v-model="searchText"
          @click:clear="searchText = ''"
          placeholder="Search products ..."
          class="mt-5 mr-4"
          style="max-width: 350px"
          prepend-inner-icon="mdi-magnify"
          clearable
          outlined
          rounded
          dense
          hide-details
        />

        <v-btn class="mt-4 mr-4 ml-4 snipcart-checkout" icon>
          <v-icon>mdi-cart</v-icon>
          <span class="snipcart-total-price"></span>
        </v-btn>
      </v-app-bar>
      <v-navigation-drawer v-model="drawer" absolute bottom temporary>
        <!-- nav items here -->
      </v-navigation-drawer>
      <v-sheet
        id="scrolling-techniques-2"
        class="overflow-y-auto"
        max-height="600"
      >
        <v-container style="height: 120px"></v-container>
      </v-sheet>
      <slot />
    </div>
    <div
      hidden
      id="snipcart"
      data-api-key="MDg5MmMwOWQtOTIxZi00ZTE4LWE3MmUtNDlkZjcyZmQ2OThjNjM3Mzg2NDU1MDUyODI0NjM2"
    ></div>
    <Footer />
  </v-app>
</template>

<script>
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Footer,
  },
  data() {
    return {
      totalPrice: 0,
    };
  },

  methods: {
    getTotalPrice() {
      return Snipcart.store.getState().cart.total;
    },
  },

  mounted() {
    this.totalPrice = this.getTotalPrice();
  },
};
</script>
<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>
