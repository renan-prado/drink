<template>
  <div class="loading">
    <img src="https://loading.io/spinners/typing/lg.-text-entering-comment-loader.gif" alt="Loading...">
  </div>
</template>

<script>
export default {
  name: 'Loading',
};
</script>

<style scoped lang="scss">
  .loading {
    text-align: center;
  }

  @media screen and (max-width: 720px) {
    img {
      width: 100px;
    }
  }
</style>
