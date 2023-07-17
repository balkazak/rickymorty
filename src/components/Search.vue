<template>
  <div class="search">
    <div class="container">
      <div class="col-md-4 offset-md-4">
        <div class="input-group mb-3">
          <span class="input-group-text" id="basic-addon1"><i class="bi bi-search"></i></span>
          <input type="text" class="form-control" placeholder="Поиск" v-model="searchText" @input="getSearchText" >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BaseInput',
  emits: ['submit'],
  data() {
    return {
      searchText: '',
    };
  },
  methods: {
    empty(){
      this.searchText = ''
    },
    getSearchText(evt) {
      const input = evt.target;

      let handle = input.dataset.handle;
      if (handle) {
        clearTimeout(handle);
      }

      handle = setTimeout(() => {
        if (this.searchText) {
          this.$emit('submit', this.searchText);
        }
      }, 1000);

      input.dataset.handle = handle;
    },
  },
};
</script>

<style scoped>

.form-control {
  border-left: none;
}
.search {
  padding: 40px 0 0;
}
input:focus, input:active {
  outline: none !important;
  box-shadow: none;
  border-color: #dee2e6;
}
.input-group-text {
  padding-right: 0;
}
</style>
