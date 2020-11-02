<template>
  <Layout>
    <template>
      <v-carousel
        cycle
        height="400"
        hide-delimiter-background
        :show-arrows="false"
      >
        <v-carousel-item v-for="(image, i) in images" :key="i">
          <v-sheet height="100%">
            <v-row class="fill-height" align="center" justify="center">
              <div class="display-3">
                <img :src="image" />
              </div>
            </v-row>
          </v-sheet>
        </v-carousel-item>
      </v-carousel>
      <Products show="false" banner="Best Sellers" />
    </template>
  </Layout>
</template>

<page-query>
query{
  products: allProduct{
    edges{
      node{
        id,
        title,
        description,
        rating,
        price,
        image
      }
    }
  }
}
</page-query>

<script>
import Products from "@/components/Products.vue";
export default {
  metaInfo: {
    title: "Mealzers",
  },
  components: {
    Products,
  },
  data() {
    return {
      images: [
        "https://bit.ly/33Ehev5",
        "https://bit.ly/33Ehev5",
        "https://bit.ly/33Ehev5",
        "https://bit.ly/33Ehev5",
      ],
    };
  },
};
</script>
