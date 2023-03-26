<template>
  <div class="home">
    <!-- header -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" />
    <div>
    <img class="logo" alt="Vue logo" src="../assets/baeminlogo.png">
    <img class="logo2" alt="Vue baemins" src="@/assets/배민외식업광장.jpg">
    <!-- 장사 캘린더 ~ 식재료 비품 -->
      <div>
        <navigation></navigation>
      </div>
      <!-- 장사 캘린더 ~ 식재료 비품 -->
    </div>
    <!-- header -->
    <!-- body -->
    <div class="Body">
        <!-- 검색창 -->
        <div class="search-container">
          <input type="text" v-model="query" @input="search" placeholder="원하는 메뉴를 검색해보세요.">
          <i class="search-icon fas fa-search" @click="search"></i>
          <ul v-if="results.length">
            <li v-for="(result, index) in results" :key="index">{{ result }}</li>
          </ul>
        </div>
        <!-- 검색창 -->
        <div class="body_right">
          <!-- 로그인창 -->
          <div class="Member__LoginBox">
            <p class="h6 mb-1">로그인을 해주세요.</p>
            <a target="_self" block="1" class="Button__StyledButton" href="">배민외식업광장 로그인</a>
            <div class="Member__Links">
              <a href="/find-account">아이디·비밀번호 찾기</a>
              <a href="/join">회원가입</a>
            </div>
          </div>
          <!-- 로그인창 -->
          <!-- 사전신청 -->
          <div class="bodyEvent">
            <a target="_blank" class="styled event1" href="/event">
              <p class="styled_ event2">사전 신청하면 선물도 드려요</p>
              <h2 color="#fff" class="styled_ event3">배민외식업박람회 2023<br></h2>
            </a>
          </div>
          <!-- 사전신청 -->
        </div>
    </div>
    <div class="body_lfet">
      <!-- 슬라이드 -->
      <div>
            <div class="slider">
              <img :src="currentImage" :alt="currentImageAlt" class="slider__image">
              <div class="slider__controls">
                <button class="slider__button" @click="prevImage" :disabled="currentIndex === 0">이전</button>
                <button class="slider__button" @click="nextImage" :disabled="currentIndex === images.length - 1">다음</button>
              </div>
            </div>
          </div>
          <!-- 슬라이드 -->
    </div>
    <!-- body -->
  </div>
</template>

<script>
import axios from 'axios'
import NavigationView from '@/views/home/navigationView.vue'

export default {
  components: {
    navigation: NavigationView
  },
  data () {
    return {
      query: '',
      results: [],
      // 슬라이드
      images: [
        {
          src: require('@/assets/삼겹살.jpg'),
          alt: 'Image 1'
        },
        {
          src: require('@/assets/양고기.jpg'),
          alt: 'Image 2'
        },
        {
          src: require('@/assets/햄버거.jpg'),
          alt: 'Image 3'
        },
        {
          src: require('@/assets/도넛.jpg'),
          alt: 'Image 4'
        }
      ],
      currentIndex: 0
      // 슬라이드
    }
  },
  methods: {
    // 검색 서버연결
    async search () {
      try {
        const response = await axios.get('https://baeminvue.netlify.app/', {
          params: {
            query: this.query
          }
        })
        this.results = response.data
      } catch (error) {
        console.error(error)
      }
      // 검색 서버연결
    },
    // 슬라이드
    prevImage () {
      if (this.currentIndex > 0) {
        this.currentIndex -= 1
      }
    },
    nextImage () {
      if (this.currentIndex < this.images.length - 1) {
        this.currentIndex += 1
      }
    }
    // 슬라이드
  },
  computed: {
    currentImage () {
      return this.images[this.currentIndex].src
    },
    currentImageAlt () {
      return this.images[this.currentIndex].alt
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
/* 로그인 */
.Member__LoginBox {
  border: 3px solid #ccc;
  padding: 20px;
  width: 300px;
  float: right;
  margin-right: 60px;
}

.Member__LoginBox p {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 10px;
  text-align: center;
}

.Button__StyledButton {
  background-color: #1ecff7;
  border-radius: 3px;
  color: #fff;
  display: block;
  font-size: 16px;
  margin-bottom: 10px;
  padding: 10px;
  text-align: center;
  text-decoration: none;
  width: 100%;
}

.Button__StyledButton:hover {
  background-color: #e6840e;
}

.Member__Links {
  text-align: center;
}

.Member__Links a {
  color: #666;
  font-size: 14px;
  margin-right: 10px;
  text-decoration: none;
}

.Member__Links a:hover {
  text-decoration: underline;
}
/* 로그인 */
/* 슬라이드 */
.slider {
  display: block;
  position: relative;
  width: 1000px;
  height: 400px;
  margin-left: 15px;
  margin-top: -190px
}

.slider__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.slider__controls {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
}

.slider__button {
  margin: 0 10px;
  background-color: #00e1ff;
  border: 1px solid #000;
  padding: 1px;
  cursor: pointer;
  outline: none;
}

.slider__button:disabled {
  opacity: 0.3;
  cursor: not-allowed;
}
/* 슬라이드 */
/* event */
.event1 {
  display: inline-block;
  flex-direction: column;
  -webkit-box-pack: center;
  justify-content: center;
  min-height: 80px;
  background: url(https://ceoimg.cdn.baemin.com/ceoimg-ym4g/i/2023/3/10/01gv585sqd2vce2tewcxwnrea7.png) right 24px bottom 50% / auto 100% no-repeat rgb(81, 114, 255);
  padding: 14px 112px 14px 24px;
  border-radius: 4px;
  width: 350px;
  margin-left: 80%;
  margin-top: 5px;
}

a {
  text-decoration: none;
  color: inherit;
  background-color: transparent;
}

a:-webkit-any-link {
  color: -webkit-link;
  cursor: pointer;
  text-decoration: underline;
}

.event2 {
  opacity: 0.88;
  font-size: 12px;
  line-height: 20px;
  letter-spacing: -0.2px;
  color: rgb(255, 255, 255);
  display: block;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  -webkit-line-clamp: 1;
}

.event3 {
  color: rgb(255, 255, 255);
  font-weight: 500;
  font-size: 16px;
  letter-spacing: -0.4px;
  line-height: 24px;
  display: block;
  overflow: hidden;
  text-overflow: ellipsis;
  max-height: 3em;
  -webkit-line-clamp: 2;
}

h2 {
  display: block;
  font-size: 1.5em;
  margin-block-start: 0.83em;
  margin-block-end: 0.83em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  font-weight: bold;
}

h1, .h1, h2, .h2, h3, .h3, h4, .h4, h5, .h5, h6, .h6 {
  margin-top: 0px;
  margin-bottom: 0px;
  font-weight: normal;
}

h1, h2, h3, h4, h5, h6 {
  font-weight: normal;
}
/* event */
</style>
