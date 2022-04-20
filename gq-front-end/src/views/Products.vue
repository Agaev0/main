<template>
  <div>
    <h1>Products</h1>
    <div v-for="p in Products" :key="p.id">
      <p>{{ p.id }}</p>
      <p>{{ p.title }}</p>
      <p>{{ p.description }}</p>
      <img :src="'http://localhost:8055/assets/'+ p.image" alt=""/>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
export default {
  apollo: {
    Products: {
      query: gql`
        query products {
      products {
        id
        title
        price
        description
        image
        }
        }

      `,
    },
  },
  data() {
    return {
      limit: 10,
    };
  },
  methods: {
    move(id) {
      this.$router.push("/products/" + id);
    },
  }
};
</script>

<style scoped>
.cart {
  border: 1px solid black;
  padding: 10px;
}
</style>