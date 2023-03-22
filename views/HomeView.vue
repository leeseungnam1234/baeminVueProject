<template>
  <div class="home">
    <!-- header -->
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
      <!-- 장사 캘린더 ~ 식재료 비품 -->
      <div>
        <ul class="navigation">
          <li v-for="(item, index) in navigationItems" :key="index">
            <a :href="item.link" v-if="!item.tooltip">{{ item.text }}</a>
            <div class="tooltip">
              <a :href="item.link" v-if="item.tooltip">{{ item.text }}</a>
              <span class="tooltip-text" v-if="item.tooltip">{{ item.tooltip }}</span>
              <ul v-if="item.dropdown">
                <li v-for="(dropdownItem, dropdownIndex) in item.dropdown" :key="dropdownIndex">
                  <a :href="dropdownItem.link">
                    <span class="icon {{ dropdownItem.icon }}"></span>
                    {{ dropdownItem.text }}
                  </a>
                </li>
              </ul>
            </div>
          </li>
        </ul>
      </div>
      <!-- 장사 캘린더 ~ 식재료 비품 -->
    </div>
    <!-- header -->
    <!-- body -->
    <div>
      <div class="Member__LoginBox">
        <p class="h6 mb-1">로그인을 해주세요.</p>
        <a target="_self" block="1" class="Button__StyledButton" href="">배민외식업광장 로그인</a>
        <div class="Member__Links">
          <a href="/find-account">아이디·비밀번호 찾기</a>
          <a href="/join">회원가입</a>
        </div>
      </div>
    </div>
    <!-- 슬라이드 -->
    <div>
      <div class="slider-container">
        <div class="slider">
          <div class="slides" :style="`transform:translateX(-${currentSlideIndex * slideWidth}px)`">
            <div v-for="(slide, index) in slides" :key="index" class="slide">
              {{ slide }}
            </div>
          </div>
        </div>
        <button @click="prevSlide">Previous</button>
        <h3>현재 슬라이드 제작중 입니다.</h3>
        <button @click="nextSlide">Next</button>
      </div>
    </div>
    <!-- 슬라이드 -->
    <!-- body -->
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      query: '',
      results: [],
      // 장사캘린더~ 배민비즈니스
      navigationItems: [
        { text: '장사캘린더', link: '/calendar', newDot: true },
        { text: '장사노하우', link: '/knowhow?page=1', tooltip: null },
        {
          text: '전문가Q&A',
          link: '/qna',
          tooltip: null
        },
        { text: '참여광장', link: '/forum', tooltip: null },
        { text: '이벤트·혜택', link: '/affiliates?progress=PROCESS&page=1', tooltip: null },
        {
          text: '배민광고',
          link: null,
          tooltip: null,
          dropdown: [
            { text: '배민광고신청', link: '/baemin-ad', icon: 'ad' },
            { text: '배민1(one)', link: '/baemin-one', icon: 'bm1' },
            { text: '배민주문접수', link: '/relaychannel', icon: 'order' },
            { text: '이용가이드', link: '/guide', icon: 'guidebook' }
          ]
        },
        { text: '식재료·비품 |', link: '/mart', tooltip: null },
        { text: '배민비즈니스', link: '/business', tooltip: null }
      ],
      // 장사캘린더~ 배민비즈니스
      // 슬라이드
      currentSlideIndex: 0,
      slides: ['Slide 1', 'Slide 2', 'Slide 3', 'Slide 4'],
      slideWidth: 500
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
    nextSlide () {
      this.currentSlideIndex =
        (this.currentSlideIndex + 1) % this.slides.length
    },
    prevSlide () {
      this.currentSlideIndex =
        (this.currentSlideIndex - 1 + this.slides.length) % this.slides.length
    }
    // 슬라이드
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

/* 장사캘린더~ 식재료 비품 */
.navigation {
  display: flex;
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.navigation li {
  margin-right: 5px;
  margin-left: 15px;
  margin-top: 10px;
  position: relative;
}

.navigation li:last-child {
  margin-right: 0;
}

.navigation li a {
  display: block;
  color: #070101;
  font-size: 18px;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.2s ease-in-out;
}

.navigation li a:hover {
  color: #00f3ee;
}

.navigation li .tooltip {
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  background-color: #23b1ca;
  color: #fff;
  border-radius: 4px;
  padding: 8px;
  font-size: 14px;
  font-weight: 400;
  text-align: center;
  opacity: 0;
  transition: all 0.2s ease-in-out;
}

.navigation li:hover .tooltip {
  opacity: 1;
  top: calc(100% + 8px);
}

.navigation li .tooltip .tooltip-text {
  display: block;
  margin-top: 4px;
  font-size: 12px;
}

.navigation li .new-dot {
  position: absolute;
  top: 5px;
  right: -10px;
  width: 10px;
  height: 10px;
  background-color: #ff4081;
  border-radius: 50%;
  display: none;
}

.navigation li:hover .new-dot {
  display: block;
}

.navigation li .dropdown {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  min-width: 200px;
  background-color: #fff;
  box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  padding: 8px;
  opacity: 0;
  visibility: hidden;
  transition: all 0.2s ease-in-out;
}

.navigation li:hover .dropdown {
  opacity: 1;
  visibility: visible;
  top: calc(100% + 8px);
}

.navigation li .dropdown a {
  display: block;
  color: #333;
  font-size: 14px;
  font-weight: 400;
  text-decoration: none;
  padding: 6px 0;
  border-bottom: 1px solid #eee;
  transition: all 0.2s ease-in-out;
  display: none;
}

.navigation li .dropdown a:last-child {
  border-bottom: none;
}

.navigation li .dropdown a:hover {
  color: #ff4081;
}

.navigation li .dropdown .icon {
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #ff4081;
  color: #fff;
  font-size: 12px;
  text-align: center;
  line-height: 20px;
  margin-right: 8px;
}
.navigation li:hover .dropdown {
  opacity: 1;
  visibility: visible;
  top: calc(100% + 8px);
  display: block;
}

li a[href='/business'] {
  color: #00f3ee;
}
/* 장사캘린더~ 식재료 비품 */
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
.slider-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.slider {
  width: 100%;
  max-width: 800px;
  height: 200px;
  margin-top: 30px;
  position: relative;
}

.slides {
  display: flex;
  height: 100%;
  transition: transform 0.3s ease-in-out;
}

.slide {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 32px;
  color: #6c0bdb;
}

.slide:nth-child(odd) {
  background-color: #219c0e;
}

.slide:nth-child(even) {
  background-color: #0dd127;
}

.slide::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: -1;
  background-color: #1b4f55;
  transform: skewX(-30deg);
}

.slide:first-child::before {
  background-color: #bd1818;
}

.slide:last-child::before {
  background-color: #ade5a0;
}

.slide-text {
  position: relative;
  z-index: 1;
  padding: 20px;
}
/* 슬라이드 */
</style>
