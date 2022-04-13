<template>
  <div>
    <hr />
    <div>
      <form @submit.prevent="onCreateItem">
        <label for="">Item</label>
        <input type="text" name="item" v-model="item" />
        <label for="">Description</label>
        <input type="text" name="description" v-model="description" />
        <button type="submit">
          {{ currentRouteName === "items" ? "Add New" : "Update" }}
        </button>
      </form>
      <br />
      <button
        @click="deleteItem"
        v-show="currentRouteName === 'items' ? false : true"
      >
        Delete
      </button>
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
          //Update item
          this.$axios
            .put(`http://127.0.0.1:8000/api/items/${this.id}`, payload)
            .then((response) => {
              console.log(response);
            });
        }
      },
      deleteItem() {
        this.$axios
          .delete(`http://127.0.0.1:8000/api/items/${this.id}`)
          .then((response) => {
            console.log(response);
          });
      },
    },
  };
</script>

<style>
</style>