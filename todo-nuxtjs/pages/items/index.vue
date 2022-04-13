<template>
  <div>
    <h1>Todo List</h1>
    <li v-for="item in items" :key="item.id">
      <NuxtLink :to="{ path: '/items/' + item.id, params: { id: item.id } }">
        {{ item.item }} | {{ item.description }}
      </NuxtLink>
    </li>
    <TodoForm />
  </div>
</template>

<script>
  export default {
    watch: {
      "$route.query": "$fetch",
    },
    async fetch() {
      const api = `http://127.0.0.1:8000/api/items/`;
      this.items = await this.$axios.$get(api);
    },
    data() {
      return {
        items: {},
      };
    },
    computed: {
      currentRouteName() {
        return this.$route.name;
      },
    },
  };
</script>

<style>
</style>