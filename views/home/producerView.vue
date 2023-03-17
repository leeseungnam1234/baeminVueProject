<template>
  <div class="portfolio">
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
        </ul>
      </section>
    </main>
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
      github: 'https://github.com/leeseungnam1234/dltmdska/tree/master',
      otherLink: 'https://play.google.com/store/apps/details?id=com.lsn.Bbangdaengkun&hl=ko',
      otherLinkText: '기타 링크(구글플레이 게임)'
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
</style>
