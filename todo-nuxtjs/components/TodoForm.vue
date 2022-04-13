<template>
  <div>
    <hr />
    <div>
      current route: {{ currentRouteName }}
      <form @submit.prevent="onCreateItem">
        <label for="">Item</label>
        <input type="text" name="item" v-model="item" />
        <label for="">Description</label>
        <input type="text" name="description" v-model="description" />
        <button type="submit">
          {{ currentRouteName === "items" ? "Submit" : "Update" }}
        </button>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    computed: {
      currentRouteName() {
        return this.$route.name;
      },
    },
    props: ["todoItem", "todoDescription", "todoId"],
    data() {
      return {
        item: this.todoItem,
        description: this.todoDescription,
        id: this.todoId,
      };
    },
    methods: {
      onCreateItem() {
        const payload = { item: this.item, description: this.description };

        if (this.currentRouteName === "items") {
          //Create new item
          this.$axios
            .post("http://127.0.0.1:8000/api/items/", payload)
            .then((response) => {
              console.log(response);
            });
        } else {
          this.$axios
            .put(`http://127.0.0.1:8000/api/items/${this.id}`, payload)
            .then((response) => {
              console.log(response);
            });
        }
      },
    },
  };
</script>

<style>
</style>