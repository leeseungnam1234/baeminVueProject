<template>
  <div class="home">
    <div>
    <img class="logo" alt="Vue logo" src="../assets/baeminlogo.png">
    <img class="logo2" alt="Vue baemins" src="@/assets/배민외식업광장.jpg">
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
    }
  }
}
</script>

<style scoped>
.logo {
  width: 180px;
  height: 100px;
  /* float: left; */
  margin: 10px;
}

.logo2 {
  width: 200px;
  height: 60px;
  /* float: left; */
}

img {
  margin-inline: 3% 1%;
  writing-mode: horizontal-tb;
  direction: rtl;
  /* float: left; */
  flex-direction: column;
}
</style>
