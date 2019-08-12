<template>
  <div class="home">
    <header-top></header-top>

    <search-result v-if="!loading" :drinks="drinks"></search-result>
    <loading v-else></loading>

  </div>
</template>

<script>
/* eslint-disable */
// @ is an alias to /src
import HeaderTop from '@/components/Header.vue';
import SearchResult from '@/components/SearchResult.vue';
import Loading from '@/components/Loading.vue';

export default {
  name: 'home',

  components: {
    HeaderTop,
    SearchResult,
    Loading,
  },

  data() {
    return {
      drinks: [],
      loading: false,
    }
  },

};
</script>

<style lang="scss" scoped>
@import "@/assets/sass/global.scss";
</style>
