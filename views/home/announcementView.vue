<template>
  <div class="notice">
    <h2>공지사항</h2>
    <ul>
      <li v-for="(notice, index) in notices" :key="index">
        <h3>{{ notice.title }}</h3>
        <p>{{ notice.content }}</p>
        <small>{{ notice.date }}</small>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      notices: [
        {
          title: '첫 번째 공지사항',
          content: '이것은 첫 번째 공지사항입니다.',
          date: '2023-03-17'
        },
        {
          title: '두 번째 공지사항',
          content: '이것은 두 번째 공지사항입니다.',
          date: '2023-03-16'
        },
        {
          title: '세 번째 공지사항',
          content: '이것은 세 번째 공지사항입니다.',
          date: '2023-03-15'
        }
      ]
    }
  }
}
</script>

<style scoped>
.notice {
  margin: 30px;
  padding: 30px;
  border: 3px solid #cc3300;
  border-radius: 20px;
  box-shadow: 0px 10px 20px rgba(0,0,0,0.3);
  background-image: linear-gradient(to bottom, #ffffff, #e6e6e6);
}

.notice h2 {
  font-size: 48px;
  margin-bottom: 40px;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 2px;
  color: #cc3300;
  text-shadow: 2px 2px 5px #ccc;
}

.notice ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.notice li {
  margin-bottom: 60px;
  border-bottom: 2px dotted #cc3300;
  padding-bottom: 30px;
}

.notice h3 {
  font-size: 32px;
  margin-bottom: 20px;
  font-weight: bold;
  color: #cc3300;
  text-shadow: 1px 1px 3px #ccc;
}

.notice p {
  font-size: 24px;
  line-height: 1.8;
  margin-bottom: 40px;
  color: #333;
  text-shadow: 1px 1px 3px #fff;
}

.notice small {
  font-size: 16px;
  color: #666;
  display: block;
  margin-top: 20px;
  text-align: right;
  text-shadow: 1px 1px 3px #ccc;
}

@media (max-width: 768px) {
  .notice {
    margin: 10px;
    padding: 20px;
  }

  .notice h2 {
    font-size: 36px;
    margin-bottom: 30px;
  }

  .notice li {
    margin-bottom: 30px;
  }

  .notice h3 {
    font-size: 24px;
    margin-bottom: 10px;
  }

  .notice p {
    font-size: 20px;
    margin-bottom: 20px;
  }

  .notice small {
    font-size: 14px;
  }
}
</style>
