<template>
  <div>
    <header>
      <h3>Navigation</h3>
      <NuxtLink to="/" class="link">Home</NuxtLink>
      <NuxtLink to="/items" class="link">Todo List</NuxtLink>
      <NuxtLink to="/about" class="link">About Us</NuxtLink>
      <NuxtLink to="/contact" class="link">Contact Us</NuxtLink>
    </header>
    <nuxt />
  </div>
</template>

<script>
  export default {
    name: "default",
  };
</script>
