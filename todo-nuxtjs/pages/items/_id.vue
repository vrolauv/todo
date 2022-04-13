<template>
  <div>
    <h1>Todo: {{ item.item }}</h1>
    <p>Description: {{ item.description }}</p>
    <TodoForm
      v-bind:todoItem="item.item"
      v-bind:todoDescription="item.description"
      v-bind:todoId="item.id"
    />
  </div>
</template>

<script>
  // export default {
  //   async fetch({ params, $axios }) {
  //     const api = `http://127.0.0.1:8000/api/items/${params.id}`;
  //     this.item = await this.$axios.$get(api);
  //   },
  //   data() {
  //     return {
  //       item: {},
  //     };
  //   },
  // };

  export default {
    async asyncData({ params, $axios }) {
      const api = `http://127.0.0.1:8000/api/items/${params.id}`;
      const item = await $axios.$get(api);
      return { item };
    },
  };
</script>

<style>
</style>