<template>
  <header>
    <div class="logo">
      <img
        src="https://cdn.vox-cdn.com/thumbor/gUhLF2JDxs-GH4njAQmSo7bHPEk=/0x0:1280x720/1200x800/filters:focal(538x258:742x462):no_upscale()/cdn.vox-cdn.com/uploads/chorus_image/image/62980013/netflix.0.gif"
        alt=""
        width="200px"
      />
    </div>
    <form>
      <input v-model="select" type="text" placeholder="Search a Film" />
      <button @click.prevent="$emit('search-film', select)">
        <i class="fas fa-search"></i>
      </button>
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