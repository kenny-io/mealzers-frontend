<template>
  <div>
    <h1
      v-if="show"
      align="center"
      justify="center"
      class="py-5 orange white--text"
    >
      {{ banner }}
    </h1>
    <v-container class="mb-3">
      <v-row :align="align" no-gutters>
        <v-col md="4" v-for="edge in $page.products.edges" :key="edge.node.id">
          <g-link
            :to="`/products/${edge.node.id}`"
            style="text-decoration: none; color: inherit"
          >
            <v-card :loading="loading" class="ma-3" shaped>
              <v-img height="250" :src="edge.node.image"></v-img>
              <v-card-title>{{ edge.node.title }}</v-card-title>
              <v-card-text>
                <v-row align="center" class="mx-0">
                  <v-rating
                    :value="edge.node.rating"
                    color="amber"
                    dense
                    half-increments
                    readonly
                    size="14"
                  ></v-rating>
                </v-row>

                <div class="my-4 subtitle-1">$ {{ edge.node.price }}</div>

                <div>
                  {{ `${edge.node.description.slice(0, 120)}...` }}
                </div>
              </v-card-text>

              <v-card-actions>
                <v-btn
                  rounded
                  outlined
                  color="orange"
                  text
                  class="snipcart-add-item"
                  :data-item-id="edge.node.id"
                  :data-item-description="edge.node.description"
                  :data-item-image="edge.node.image"
                  :data-item-price="edge.node.price"
                  :data-item-name="edge.node.title"
                >
                  Add to cart
                </v-btn>
              </v-card-actions>
            </v-card>
          </g-link>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  props: ["banner", "show"],
};
</script>
