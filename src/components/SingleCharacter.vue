<template>
  <div class="container">
    <div class="col-md-4 offset-md-4">
      <div class="item d-flex align-items-center justify-content-between">
        <div class="d-flex align-items-center">
          <img :src="image" :alt="alt" class="avatar">
          <div class="name">{{ name }}</div>
        </div>
        <img @click="alertInfo" src="../assets/images/notification-message.svg" class="img-fluid notification" alt="notification">
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: ['image', 'alt', 'name', 'species'],
  methods: {
    async alertInfo() {
      alert(this.species)
    },
  }
}
</script>

<style scoped>
.item {
  margin: 30px 0;
  width: 100%;
}

.notification {
  width: 15px;
  cursor: pointer;
}
.avatar {
  max-width: 50px;
  max-height: 50px;
  border-radius: 50px;
  margin-right: 20px;
}
.name {
  font-weight: 700;
  font-size: 17px;
}
</style>