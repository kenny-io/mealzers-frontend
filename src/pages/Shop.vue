<template>
  <Layout>
    <Products />
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
        image,
        price
      }
    }
  }
}
</page-query>

<script>
import Products from "../components/Products";
export default {
  components: {
    Products,
  },
};
</script>
