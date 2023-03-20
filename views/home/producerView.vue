<template>
  <div class="portfolio">
    <div>
      <header>
        <h1>{{ name }}</h1>
        <p>{{ description }}</p>
      </header>
      <main>
        <section class="projects">
          <h2>프로젝트 목록</h2>
          <ul>
            <li v-for="project in projects" :key="project.id">
              <h3>{{ project.name }}</h3>
              <p>{{ project.description }}</p>
              <p>전화번호: {{ phoneNumber }}</p>
              <p>이메일: {{ email }}</p>
              <p>사는 곳: {{ address }}</p>
              <a :href="project.link">프로젝트 바로가기</a>
            </li>
          </ul>
        </section>
        <section class="links">
          <h2>링크</h2>
          <ul>
            <li>
              <a :href="notion">노션</a>
            </li>
            <li>
              <a :href="github">깃허브</a>
            </li>
            <li>
              <a :href="otherLink">{{ otherLinkText }}</a>
            </li>
            <li>
              <a :href="otherLink2">{{ otherLinkText2 }}</a>
            </li>
          </ul>
        </section>
      </main>
    </div>
    <!-- skill -->
    <div class="skill-item">
      <h2>Skill 목록</h2>
      <div class="status-bar-item clfix" v-for="(skill, index) in skills" :key="index">
        <div class="status-bar-item-name">{{ skill.name }}</div>
        <div class="status-bar-item-ability">
          <div :class="'percent percent-' + skill.percent + ' percent-color-' + skill.color">
            <span class="status-bar-item-percent">{{ skill.percent }}%</span>
          </div>
        </div>
      </div>
    </div>
    <!-- skill -->
  </div>
</template>

<script>
export default {
  name: 'Portfolio-page',
  data () {
    return {
      name: '이승남',
      description: '1993년 04월 16일 , 상일미디어고(컴퓨터응용과) 졸업, IT학원 Python & Java 빅데이터 front end, back end 교육 이수',
      phoneNumber: '010-9629-3082',
      email: 'dltmdska01@naver.com',
      address: '하남시 망월동 1079번지 우성르보아파크',
      projects: [
        {
          id: 1,
          name: '프로젝트 1',
          description: '배민외식업광장 따라해보기',
          link: 'https://baeminvue.netlify.app/'
        }
        // 나중에 프로젝트 추가될때 사용
        // {
        //   id: 2,
        //   name: '프로젝트 2',
        //   description: '프로젝트 2 설명',
        //   link: 'https://example.com/project2'
        // },
        // {
        //   id: 3,
        //   name: '프로젝트 3',
        //   description: '프로젝트 3 설명',
        //   link: 'https://example.com/project3'
        // }
      ],
      notion: 'https://www.notion.so/leeseungnam/b94856f51f7c483181256dabc3f8cb38?pvs=4',
      github: 'https://github.com/leeseungnam1234/baeminVueProject',
      otherLink: 'https://play.google.com/store/apps/details?id=com.lsn.Bbangdaengkun&hl=ko',
      otherLinkText: '기타 링크(구글플레이 게임)',
      otherLink2: 'https://github.com/leeseungnam1234/dltmdska',
      otherLinkText2: '기타 링크(깃허브 학원,공부 내용)',
      skills: [
        { name: 'Html', percent: 80, color: 0 },
        { name: 'Vue.js', percent: 80, color: 1 },
        { name: 'Css3', percent: 70, color: 2 },
        { name: 'jQuery', percent: 70, color: 3 },
        { name: 'JavaScript', percent: 70, color: 4 },
        { name: 'Spring', percent: 50, color: 5 },
        { name: 'Intelij(Tool)', percent: 70, color: 6 },
        { name: 'Git', percent: 60, color: 7 }
      ]
    }
  }
}
</script>

<style scoped>
/* header 스타일링 */
.portfolio {
  max-width: 800px;
  margin: auto;
  font-family: Arial, sans-serif;
  text-align: center;
  background-color: #f8f8f8;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  color: #333;
}

h2 {
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
  color: #333;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  margin-bottom: 1rem;
}

a {
  text-decoration: none;
  color: #0077cc;
  transition: all 0.2s ease-in-out;
}

a:hover {
  text-decoration: underline;
  color: #005ea8;
}

section {
  margin-top: 3rem;
}

.projects h3 {
  font-size: 2rem;
  margin-bottom: 0.5rem;
  color: #333;
}

.projects p {
  margin-bottom: 1rem;
  color: #555;
}

.links li {
  display: inline-block;
  margin-right: 1.5rem;
}

@media (max-width: 600px) {
  h1 {
    font-size: 2.5rem;
  }
  h2 {
    font-size: 1.5rem;
  }
  .projects h3 {
    font-size: 1.5rem;
  }
}

/* header 스타일링 */
header {
  margin-bottom: 2rem;
}

/* 프로젝트 목록 리스트 스타일링 */
.projects li {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 1rem;
}

.projects li:hover {
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

/* 프로젝트 목록 링크 스타일링 */
.projects a {
  display: inline-block;
  background-color: #0077cc;
  color: #fff;
  border-radius: 5px;
  padding: 0.5rem 1rem;
  margin-top: 1rem;
  transition: all 0.2s ease-in-out;
}

.projects a:hover {
  background-color: #005ea8;
}

/* 링크 리스트 스타일링 */
.links li {
  margin-right: 2rem;
}

/* 링크 스타일링 */
.links a {
  color: #0077cc;
}

.links a:hover {
  text-decoration: none;
  color: #005ea8;
}

/* 반응형 스타일링 */
@media (max-width: 600px) {
  .projects li {
    font-size: 0.9rem;
  }
}

/* skill 스타일 */
.skill-item {
  margin: 30px auto;
  max-width: 600px;
}

.status-bar-item {
  margin: 10px 0;
  display: flex;
  align-items: center;
}

.status-bar-item-name {
  width: 120px;
  font-weight: bold;
}

.status-bar-item-ability {
  flex: 1;
  margin-left: 20px;
  position: relative;
}

.percent {
  height: 12px;
  border-radius: 6px;
  position: relative;
  overflow: hidden;
}

.percent span {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -15%);
  font-size: 12px;
  font-weight: bold;
  color: black;
}

.percent-color-0 {
  background-color: #f16529;
}

.percent-color-1 {
  background-color: #41b883;
}

.percent-color-2 {
  background-color: #3c8dbc;
}

.percent-color-3 {
  background-color: #f0ad4e;
}

.percent-color-4 {
  background-color: #007aff;
}

.percent-color-5 {
  background-color: #6db33f;
}

.percent-color-6 {
  background-color: #3b5998;
}

.percent-color-7 {
  background-color: #6e5494;
}

.percent-80 {
  width: 80%;
}

.percent-70 {
  width: 70%;
}

.percent-60 {
  width: 60%;
}

.percent-50 {
  width: 50%;
}

.status-bar-item-value {
  margin-left: 10px;
  font-size: 12px;
  font-weight: bold;
}

.percent .status-bar-item-percent {
  position: absolute;
  right: 0;
  top: 0;
  padding: 0 4px;
  font-size: 12px;
  font-weight: bold;
  color: rgb(27, 4, 4);
}
</style>
