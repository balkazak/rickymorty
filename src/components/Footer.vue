<template>
 <div class="container">
   <div class="col-md-4 offset-md-4">
     <div class="footer">
       <div class="menu-item">
         <img src="../assets/images/icons/navigator.svg" alt="navigation">
         <p>Пункт</p>
       </div>
       <div class="menu-item">
         <img src="../assets/images/icons/chat.svg" alt="chat">
         <p>Пункт</p>
       </div>
       <div class="menu-item">
         <img src="../assets/images/icons/clock.svg" alt="clock">
         <p>Пункт</p>
       </div>
       <div class="menu-item">
         <img src="../assets/images/icons/user.svg" alt="user">
         <p>Пункт</p>
       </div>
     </div>
   </div>
 </div>
</template>

<style scoped>
  .footer {
    padding: 20px 50px;
    display: flex;
    justify-content: space-between;
    border-radius: 30px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    margin-top: 20px;
  }
  p {
    font-size: 12px;
    margin: 0;
  }
  .menu-item {
    text-align: center;
    cursor: pointer;
  }
</style>
<script setup>
</script>