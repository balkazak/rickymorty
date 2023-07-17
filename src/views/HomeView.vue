<template>
  <main>
    <h1>Персонажи</h1>
    <Search ref="searchbar" @submit="doSearch" />
    <div v-if="result.info?.count" class="text-center count">
      {{result.info?.count}} персонажей
    </div>
    <ResultList ref="list" :error="error" :data="result" />
    <button v-if="clearBtnShow" @click="clear" type="button" class="btn btn-lg btn-block">Сбросить поиск</button>
  </main>
</template>

<script>
  import ResultList from '@/components/ResultList.vue';
  import Search from '@/components/Search.vue';
  import axios from 'axios'

export default {
  name: 'TheSearchForm',
  components: { Search, ResultList },
  data() {
    return {
      result: [],
      error: false,
      clearBtnShow: false
    };
  },
  beforeMount() {
    this.loadInitialList();
  },
  methods: {
    async loadInitialList() {
      await axios.get('https://rickandmortyapi.com/api/character')
          .then((response) => {
            this.result = response.data;
          })
    },
    clear() {
      this.result = [];
      this.$refs.searchbar.empty();
      this.$refs.list.refresh();
      this.error = false;
      this.clearBtnShow = false;
      this.loadInitialList();
    },
    async doSearch(searchText) {
      this.clearBtnShow = true;
      this.$refs.list.refresh();

      this.result = [];
      await axios.get('https://rickandmortyapi.com/api/character', {
        params: {name: searchText}
      })
          .then((response) => {
            this.error = false;
            this.result = response.data;
          })
          .catch((error) => {
            if (error) {
              this.error = true
            }
          })
    },
  }
};
</script>

<style scoped>
  h1 {
    font-size: 20px;
    color: #221A51;
    text-align: center;
    margin-top: 20px;
  }
  .count {
    color: #C1C2C7;
    margin: 20px 0;
  }
  .btn {
    background-color: #CB99FA;
    color: white;
    font-size: 20px;
    margin: 0 auto;
    display: block;
    width: 350px;
  }

@media screen and (max-width: 768px) {

}
</style>