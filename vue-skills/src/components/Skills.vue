<template>
  <div class="hello">
    <div class="holder">
      <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter a skill you have.." v-model="skill">
        <div class="advanced">Advanced
          <input type="checkbox" id="checkbox" v-model="checked">
        </div>
      </form>
        <p class="preview" v-if="skill.length > 0"> {{ skill }}</p>
      <ul>
        <li v-for="(data, index) in skills" :key='index'>{{ index }}. {{ data.skill }} 
          <span v-if="data.checked">Advanced</span>
        </li>
      </ul>
<!-- 
<p v-if="skills.length > 1">You have more than 1 skills</p>
<p v-else>You have less than or equal to 1 skill</p>
-->
<!-- 
      <div v-bind:class="alertObject" v-if="alertObject.alert">THIS IS AN ALERT</div>
-->
      <p>These are the skills that you possess.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      checked: false,
      skill: '',
      skills: [
      ],
      /*
      alertObject: {
        alert: true
      }
      */
    }
  },
  methods: {
    addSkill() {
      this.skills.push({skill: this.skill, checked: this.checked}),
      this.skill = '',
      console.log('This checkbox value is: '+this.checked),
      this.checked = false;
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style src="./Skills.css" scoped />