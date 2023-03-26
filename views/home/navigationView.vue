<template>
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
</template>

<script>
export default {
  data () {
    return {
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
      ]
      // 장사캘린더~ 배민비즈니스
    }
  }
}
</script>

<style>
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
/* 슬라이드 */
</style>
