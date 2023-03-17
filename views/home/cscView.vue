<template>
  <div class="customer-service">
    <h2>고객센터</h2>
    <div class="container">
      <div class="left">
        <ul>
          <li
            v-for="(category, index) in categories"
            :key="index"
            :class="{ active: activeCategory === index }"
            @click="activeCategory = index"
          >
            <span>{{ category }}</span>
          </li>
        </ul>
      </div>
      <div class="right">
        <h3>{{ categories[activeCategory] }}</h3>
        <ul>
          <li v-for="(question, index) in questions" :key="index">
            <h4>{{ question.title }}</h4>
            <p>{{ question.answer }}</p>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      categories: ['배송문의', '반품/교환', '결제/취소', '상품문의', '기타문의'],
      activeCategory: 0,
      questions: [
        {
          title: '배송이 언제 이루어지나요?',
          answer: '일반적으로 주문 완료 후 1~2일 내에 배송됩니다.'
        },
        {
          title: '반품은 어떻게 하나요?',
          answer: '마이페이지에서 반품신청을 하시거나 고객센터로 문의해주세요.'
        },
        {
          title: '결제 수단은 무엇이 있나요?',
          answer: '신용카드, 계좌이체, 휴대폰 결제 등이 있습니다.'
        },
        {
          title: '상품 문의는 어디서 할 수 있나요?',
          answer: '상품페이지 하단의 Q&A 혹은 고객센터를 이용해주세요.'
        },
        {
          title: '기타 문의사항은 어떻게 해야 하나요?',
          answer: '고객센터로 연락주시면 친절하게 안내해드리겠습니다.'
        }
      ]
    }
  }
}
</script>

<style scoped>
.customer-service {
  margin: 30px;
}

.customer-service h2 {
  font-size: 36px;
  margin-bottom: 20px;
  text-align: center;
  font-weight: 600;
}

.customer-service .container {
  display: flex;
  justify-content: space-between;
  margin-top: 50px;
}

.customer-service .left {
  width: 250px;
  background-color: #f4f4f4;
  border-radius: 10px;
  overflow: hidden;
}

.customer-service .left ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.customer-service .left li {
  padding: 20px;
  cursor: pointer;
  transition: background-color 0.3s;
  font-size: 20px;
  font-weight: 500;
  border-bottom: 1px solid #ccc;
}

.customer-service .left li:last-child {
  border-bottom: none;
}

.customer-service .left li.active {
  background-color: #fff;
  border-left: 5px solid #fca311;
}

.customer-service .right {
  width: calc(100% - 300px);
}

.customer-service .right h3 {
  font-size: 28px;
  margin-bottom: 30px;
  font-weight: 600;
  color: #fca311;
}

.customer-service .right ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.customer-service .right li {
  margin-bottom: 30px;
}

.customer-service .right h4 {
  font-size: 24px;
  margin-bottom: 10px;
  font-weight: 600;
  color: #333;
}

.customer-service .right p {
  font-size: 20px;
  margin-bottom: 20px;
  line-height: 1.5;
}
</style>
