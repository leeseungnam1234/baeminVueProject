<template>
  <div class="home">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" />
    <div>
    <img class="logo" alt="Vue logo" src="../assets/baeminlogo.png">
    <img class="logo2" alt="Vue baemins" src="@/assets/배민외식업광장.jpg">
    <!-- 검색창 -->
    <div class="search-container">
      <input type="text" v-model="query" @input="search" placeholder="원하는 메뉴를 검색해보세요.">
      <i class="search-icon fas fa-search" @click="search"></i>
      <ul v-if="results.length">
        <li v-for="(result, index) in results" :key="index">{{ result }}</li>
      </ul>
    </div>
    <!-- 검색창 -->
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      query: '',
      results: []
    }
  },
  methods: {
    search () {
      // 검색 API 호출 및 결과 처리
      // this.results = ['검색 결과1', '검색 결과2', '검색 결과3']
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
  height: 65px;
  /* float: left; */
  padding: 5px;
  /* margin: 5px; */
  margin-bottom: 12px;
}

/* img {
  margin-inline: 3% 1%;
  writing-mode: horizontal-tb;
  direction: rtl;
  float: left;
  flex-direction: column;
} */

/* input[type="text"] {
  margin-left: 500px;
  width: 15%;
  box-sizing: border-box;
  padding: 2px;
  font-size: 15px;
} */
.search-container {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  position: relative;
  margin-right: 60px;
  margin-top: -70px;
}

.search-icon {
  position: absolute;
  top: 50%;
  right: 10px;
  transform: translateY(-50%);
  color: #aaa;
  cursor: pointer;
}

input[type="text"] {
  width: 300px;
  height: 35px;
  padding: 5px 30px 5px 10px;
  font-size: 15px;
  border-radius: 5px;
  border: 1px solid #aaa;
  outline: none;
  box-shadow: none;
}

input[type="text"]:focus {
  border-color: #4d90fe;
  box-shadow: 0 0 0 2px rgba(77, 144, 254, 0.2);
}
</style>
