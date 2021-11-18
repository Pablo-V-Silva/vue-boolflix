<template>
  <header>
    <form>
      <input v-model="type" type="text" placeholder="Search a Film" />
      <button @click.prevent="$emit('search-film', type)">CERCA</button>
    </form>
  </header>
</template>

<script>
export default {
  data() {
    return {
      type: "",
    };
  },
};
</script>

<style>
</style>