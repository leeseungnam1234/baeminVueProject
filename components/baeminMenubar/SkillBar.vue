<template>
  <div class="skill-item">
    <div class="status-bar-item clfix" v-for="(skill, index) in skills" :key="index">
      <div class="status-bar-item-name">{{ skill.name }}</div>
      <div class="status-bar-item-ability">
        <div :class="'percent percent-' + skill.percent + ' percent-color-' + skill.color">
          <span class="status-bar-item-percent">{{ skill.percent }}%</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SkillBar',
  data () {
    return {
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
