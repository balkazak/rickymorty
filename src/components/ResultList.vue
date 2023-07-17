<template>
  <div class="wrapper container" v-dragscroll="true">
    <div class="photos" >
      <SingleCharacter
        v-for="character in companiesLoaded"
        :key="character.id"
        :alt="character.name"
        :image="character.image"
        :name="character.name"
        :species="character.species"
      />
      <div @click="loadMore" v-if="companiesLoaded?.length < this.data.results?.length" class="more text-center">
        Показать еще
        <i class="bi bi-arrow-down"></i>
      </div>
      <div v-if="error" class="error">
        Не удалось найти персонажей <br> с таким именем
      </div>
    </div>
  </div>
</template>

<script>
import SingleCharacter from './SingleCharacter.vue';
import { dragscroll } from 'vue-dragscroll'
export default {
  data() {
    return {
      length: 6
    };
  },
  directives: {
    dragscroll
  },
  components: { SingleCharacter },
  props: ['data', 'error'],
  computed: {
    companiesLoaded() {
      return this.data.results?.slice(0, this.length);
    },
  },
  methods: {
    loadMore() {
      if (this.length > this.data.results.length) return;
      this.length = this.length + 5;
    },
    refresh(){
      console.log('refresh');
      this.length = 6;
    }
  }
};
</script>

<style scoped>

  .wrapper {
    overflow-y: auto;
    padding-bottom: 30px;
  }
  .more {
    cursor: pointer;
    color: #3C4061;
    font-weight: 700;
    font-size: 17px;
  }
  i {
    margin-left: 40px;
  }
  .error {
    color: #C1C2C7;
    font-size: 15px;
    font-weight: 400;
    text-align: center;
  }

</style>
