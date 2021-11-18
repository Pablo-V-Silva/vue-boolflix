<template>
  <header>
    <form>
      <input v-model="select" type="text" placeholder="Search a Film" />
      <button @click.prevent="$emit('search-film', select)">CERCA</button>
    </form>
  </header>
</template>

<script>
export default {
  data() {
    return {
      select: "",
    };
  },
};
</script>

<style>
</style>