<template>
  <nav>
    <router-link class="menubar" to="/baemin_selfservice">배민셀프서비스 |</router-link>
    <router-link class="menubar" to="/baemin_sanghoe">배민상회 |</router-link>
    <router-link class="menubar" to="/baemin_Academy">배민아카데미 |</router-link>
    <router-link class="menubar" to="/baemin_jangbu">배민장부 |</router-link>
    <router-link class="menubar" to="/baemin_lobos">배민로봇 |</router-link>
    <router-link class="menubar" to="/producerView">제작자 포트폴리오 |</router-link>
    <a class="menubar" href="/">메인화면</a>
    <router-link class="menubar2" to="/join">회원가입</router-link>
    <router-link class="menubar2" to="/login">로그인 |</router-link>
    <router-link class="menubar2" to="/csc">고객센터 |</router-link>  <!--customer service center = csc 로 만듬-->
    <router-link class="menubar2" to="/announcement">공지사항 |</router-link>
  </nav>
  <router-view/>
</template>

<script>
export default {
  data () {
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menubar {
  display: block;
  font-size: 20px;
  font-weight: lighter;
  font-family: cursive;
  float: left;
  text-decoration: none;
}

.menubar2 {
  display: inline-block;
  font-size: 20px;
  font-weight: lighter;
  font-family: cursive;
  float: right;
  text-decoration: none;
}

.menubar:hover {
  text-decoration: underline;
  color: #ff0909;
}

.menubar2:hover {
  text-decoration: underline;
  color: #f50909;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
