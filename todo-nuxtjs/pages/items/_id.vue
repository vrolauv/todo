<template>
  <div>
    <h1>Todo: {{ item.item }}</h1>
    <p>Description: {{ item.description }}</p>
  </div>
</template>

<script>
  export default {
    async fetch() {
      const api = `http://127.0.0.1:8000/api/items/1`;
      this.item = await this.$axios.$get(api);
    },
    data() {
      return {
        item: {},
      };
    },
  };

  //   export default {
  //     async asyncData({ params, $axios }) {
  //       const api = `http://127.0.0.1:8000/api/items/${params.id}`;
  //       const item = await $axios.$get(api);
  //       return { item };
  //     },
  //   };
</script>

<style>
</style>