<template>
  <Layout>
    <template>
      <v-card elevation="0" class="mx-auto center mt-5 mb-3" max-width="900">
        <v-img
          class="white--text align-end"
          height="200px"
          width="300px"
          :src="`http://localhost:1337${this.$page.product.image}`"
        >
        </v-img>

        <v-card-title>{{ this.$page.product.title }}</v-card-title>
        <v-card-text class="text--primary">
          <div>{{ this.$page.product.description }}</div>
        </v-card-text>
        <v-card-subtitle class="pb-0">
          <h3>Instructions</h3>
          {{ this.$page.product.instructions }}
        </v-card-subtitle>

        <v-card-actions>
          <v-btn
            rounded
            outlined
            color="orange"
            text
            class="snipcart-add-item"
            :data-item-id="this.$page.product.id"
            :data-item-description="this.$page.product.description"
            :data-item-image="
              `http://localhost:1337${this.$page.product.image}`
            "
            :data-item-price="this.$page.product.price"
            :data-item-name="this.$page.product.title"
          >
            Add to cart
          </v-btn>
          <v-spacer></v-spacer>
          <v-rating
            :value="this.$page.product.rating"
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          ></v-rating>
          <span>
            <v-card-title>${{ this.$page.product.price }}</v-card-title>
          </span>
        </v-card-actions>
      </v-card>
    </template>
    <div class="separator"></div>
  </Layout>
</template>

<page-query>
query Products($id: ID!) {
  product(id: $id) {
    id
    title
    image
    description
    price,
    instructions,
    rating
  }
}
</page-query>
<script>
export default {};
</script>
<style></style>
