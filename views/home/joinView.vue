<template>
  <div class="signup">
    <h2>회원가입</h2>
    <form>
      <div class="form-group">
        <label for="username">이름</label>
        <input type="text" id="username" v-model="username" required />
      </div>
      <div class="form-group">
        <label for="password">비밀번호</label>
        <input type="password" id="password" v-model="password" required />
      </div>
      <div class="form-group">
        <label for="confirm-password">비밀번호 확인</label>
        <input
          type="password"
          id="confirm-password"
          v-model="confirmPassword"
          required
        />
      </div>
      <div class="form-group">
        <label for="email">이메일</label>
        <input type="email" id="email" v-model="email" required />
      </div>
      <div class="form-group">
        <label for="birthday">생일</label>
        <input type="date" id="birthday" v-model="birthday" required />
      </div>
      <div class="form-group">
        <label for="gender">성별</label>
        <select id="gender" v-model="gender" required>
          <option value="">선택하세요</option>
          <option value="male">남성</option>
          <option value="female">여성</option>
          <option value="other">기타</option>
        </select>
      </div>
      <div class="form-group">
        <label for="phone">휴대폰 번호</label>
        <input type="tel" id="phone" v-model="phone" required />
      </div>
      <div class="form-group">
        <label for="address">주소</label>
        <input type="text" id="address" v-model="address" required />
      </div>
      <div class="form-group">
        <label for="occupation">직업</label>
        <input type="text" id="occupation" v-model="occupation" required />
      </div>
      <button type="submit" @click.prevent="submitForm">가입하기</button>
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      username: '',
      password: '',
      confirmPassword: '',
      email: '',
      birthday: '',
      gender: '',
      phone: '',
      address: '',
      occupation: ''
    }
  },
  methods: {
    submitForm () {
      // form submission logic here
    }
  }
}
</script>

<style scoped>
.signup {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f9fafb;
  font-family: "Noto Sans KR", sans-serif;
}

h2 {
  margin-bottom: 20px;
  font-size: 24px;
  font-weight: bold;
  text-transform: uppercase;
  color: #2c3e50;
}

form {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  width: 400px;
}

label {
  display: block;
  font-size: 16px;
  font-weight: 500;
  margin-bottom: 5px;
  color: #2c3e50;
}

input, select {
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: #f5f5f5;
  font-size: 16px;
  color: #333333;
}

button[type="submit"] {
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: #2c3e50;
  font-size: 16px;
  font-weight: bold;
  color: #ffffff;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button[type="submit"]:hover {
  background-color: #34495e;
}
</style>
