<template>
  <header>
    <nav class="d-flex align-items-center justify-content-between contain">
      <div class="logo">
        <img
          src="https://cdn.vox-cdn.com/thumbor/gUhLF2JDxs-GH4njAQmSo7bHPEk=/0x0:1280x720/1200x800/filters:focal(538x258:742x462):no_upscale()/cdn.vox-cdn.com/uploads/chorus_image/image/62980013/netflix.0.gif"
          alt=""
          width="200px"
        />
      </div>
      <form class="pe-3">
        <input
          v-model="select"
          type="text"
          placeholder="Search a Film"
          class="rounded-start"
        />
        <button @click.prevent="$emit('search-film', select)">
          <i class="fas fa-search searchBtn"></i>
        </button>
      </form>
    </nav>
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

<style lang="scss">
@import "../assets/scss/variables.scss";
header {
  background-color: $header_color;
  overflow: hidden;
  form {
    input,
    button {
      padding: 0.6rem 1rem;
      border: 1px solid white;
    }
    button {
      border-radius: 0 3px 3px 0;
      &:hover {
        background-color: rgb(90, 90, 90);
        color: white;
        transition: 0.35s;
      }
    }
  }
}
</style>