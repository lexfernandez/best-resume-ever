<template>
  <div class="resume" id="resume2">
    <div class="left-column">
      <div>
        <div class="headline">
          <span> {{ person.name.first }} {{ person.name.middle }} </span>
          <span> {{ person.name.last }} </span>
        </div>

        <p>
          <span class="txt-full-white"> {{ person.position }} </span>
          <br/>
          <span> {{ person.contact.city }} </span>
        </p>
      </div>

      <div class="multi-line-txt">
        {{ person.about }}
      </div>

      <div class="multi-line-txt">
        {{ person.knowledge }}
      </div>
      <span class="section-headline white-color">{{ lang.contact }} </span>
      <a :href="'mailto:' + person.contact.email">
        <div class="block-marged txt-full-white without-margin">
          <i class="material-icons white-color">mail</i>  {{ person.contact.email }}
        </div>
      </a>

      <div class="block-marged txt-full-white without-margin">
        <i class="material-icons white-color">phone</i>  {{ person.contact.phone }}
      </div>

      <div class="social-container without-margin">
        <a v-if="person.contact.website"
          :href="person.contact.website">

          <div class="block-marged txt-full-white without-margin">
            <i class="fa fa-globe contact-icon"></i>
            {{ person.contact.website }}
          </div>
        </a>

        <a v-if="person.contact.github"
          :href="'https://github.com/' + person.contact.github"
          class="external-link">

          <span class="block-marged txt-full-white without-margin"><i class="fa fa-github contact-icon"></i>  {{ person.contact.github }}</span>
        </a>

        <a v-if="person.contact.codefights"
          :href="'https://codefights.com/profile/' + person.contact.codefights"
          class="external-link">

          <svg width="20" height="20" viewBox="0 0 24 24"
            class="contact-icon-svg">
            <path d="M12 15.2L9.2 4.8 0 3.2l1.7 2.6 5.7.7.7 2.3-3.7-.4 1.3 2 3 .3L12 20.8l3.3-10.1 3-.3 1.3-2-3.7.4.7-2.3 5.7-.7L24 3.2l-9.2 1.6">
            </path>
          </svg>

          <span class="block-marged txt-full-white">
            {{ person.contact.codefights }}
          </span>
        </a>

        <a v-if="person.contact.medium"
          :href="'https://medium.com/@' + person.contact.medium"
          class="external-link">
          <i class="fab fa-medium contact-icon"></i>
          <span class="block-marged txt-full-white">
            {{ person.contact.medium }}
          </span>
        </a>
      </div>

      <div class="hobbies-container">
        <!-- <span class="subheadline">Hobbies</span> -->
        <div class="hobbies-content">
          <a v-for="(hobby, index) in person.hobbies" :key="index"
            class="hobby-item"
            :href="hobby.url">

            <i v-if="hobby.iconClass" :class="hobby.iconClass + ' hobby-item__icon'"></i>
            <span class="hobby-item__icon-label"> {{ hobby.name }} </span>
          </a>
        </div>
      </div>

      <div class="content">
        <div class="content__left">
          <div
              v-if="person.skills"
              class="section">
              <div class="icon">
                <i class="material-icons white-color">done_all</i>
                <span class="section-headline white-color"> {{ lang.skills }} </span>
              </div>
              <div class="section-content skills-content">
                <a
                  v-for="(skill, index) in person.skills"
                  class="grid-item"
                  :key="index"
                  :href="skill.url">
                  <span class="squarred-grid-item">
                    {{ skill.name }}
                  </span>
                </a>
              </div>
            </div>
          </div>
        </div>
    </div>

    <div class="left-column-bg">
      <!-- <div><a href="/otot">toto</a></div> -->
    </div>

    <div class="right-column">
      <div class="experience-section section">
        <div class="icon">
          <i class="material-icons small-icon">work</i>
          <span class="section-headline">{{ lang.experience }}</span>
        </div>

        <div class="section-content">
          <a v-for="(experience, index) in person.experience" :key="index"
            class="section-content__item"
            :href="experience.website">

            <span class="section-content__header"> {{ experience.position }}</span>
            <span class="section-content__subheader"> {{ experience.company }}</span>
            <span class="section-content__text--light"> {{ experience.description }}</span>
          </a>
        </div>
      </div>

      <div v-if="person.projects"
        class="projects-section section">
        <div class="icon">
          <i class="material-icons">code</i>
          <span class="section-headline"> {{ lang.projects }} </span>
        </div>

        <div class="section-content">
          <a v-for="(project, index) in person.projects" :key="index"
            class="section-content__item"
            :href="project.url">

            <span class="section-content__header"> {{ project.name }} </span>
            <span class="section-content__subheader">{{ project.platform }}</span>
            <span class="section-content__text"> {{ project.description }} </span>
            <span class="section-content__text--light"> {{ project.url }} </span>
          </a>
        </div>
      </div>

      <div class="education-section section">
        <div class="icon">
          <i class="material-icons">school</i>
          <span class="section-headline">{{ lang.education }}</span>
        </div>

        <div class="section-content">
          <a v-for="(education, index) in person.education" :key="index"
            class="section-content__item"
            :href="education.website">

            <span class="section-content__header"> {{ education.school }} </span>
            <span class="section-content__subheader">{{ education.degree }}</span>
            <span class="section-content__text"> {{ education.timeperiod }} </span>
            <span class="section-content__text--light"> {{ education.description }} </span>
          </a>
        </div>
      </div>

      <div v-if="person.contributions"
        class="contributions-section section">

        <div class="icon">
          <i class="fa fa-heart font-awesome-icons"></i>
          <span class="section-headline"> {{lang.contributions}} </span>
        </div>

        <div class="section-content-grid">
          <a v-for="(contribution, index) in person.contributions" :key="index"
            :href="contribution.url"
            class="section-content__item-grid">

            <span class="section-content__header"> {{ contribution.name }} </span>
            <span class="section-content__text"> {{ contribution.description }} </span>
            <span class="section-content__text--light" style="word-break: break-all;">
              {{ contribution.url }}
            </span>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'creative';

export default Vue.component(name, getVueOptions(name));
</script>

<style lang="less" scoped>

@accent-color: #34495E;

.resume {
  display: flex;
  position: relative;

  font-family:'Roboto' !important;
  font-size: 0.9em;
}

.left-column {
  width: 30%;
  height: 100%;
  padding: 30px;
  padding-top: 45px;
  text-align: left;

  color: #ffffff;
  color:rgba(255,255,255,0.70);
  background-color: @accent-color;
  overflow: hidden;
  display: block;
  z-index: 2;

  opacity: 1; // lower this value (0.7 approx.) to see the cover image
  position: absolute;
}

// Background cover displayed on the left-column side
// ------------
.left-column-bg {
  // You can put your own cover image in the url path
  // --------------------------------------
  // background: url('../assets/cover.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 25% 25%;
  opacity: .4; // up this value to contrast the cover image

  height: 100%;
  width: 35%;
  padding: 30px;
  padding-top: 45px;

  display: block;
  overflow: hidden;
  position: relative;
  top: 0;
  z-index: 1;
}

.right-column {
  display: flex;
  flex-direction: column;
  padding: 30px;

  height: 100%;
  width: 65%;
}

a {
  color: inherit;
  cursor:pointer;
  text-decoration-line: none;

  &:visited {
    color: inherit;
  }
}

.material-icons {
  color: @accent-color;
  position: relative;
  top: 5px;
}

.font-awesome-icons {
  color: @accent-color;
  font-size: 1.3em;
  margin-right: 6px;
}

.small-icon {
  top: 2.5px;
  font-size: 1.4em;
}

.contact-icon {
  color: white;
  font-size: 1.5em;
  margin-right: 10px;

  top: 2px;
  position: relative;
}

.contact-icon-svg {
  margin-top: -2.5px;
  margin-right: 10px;

  transform: scale(1);

  top: 5px;
  position: relative;
}

.contact-icon-svg path {
  fill: white;
}

.external-link {
  display: block;
  margin-bottom: 5px;
}

.block-marged {
  margin-top: 15px;
  margin-bottom: 15px;
}

.multi-line-txt {
  margin-top: 30px;
  margin-bottom: 20px;
}

.social-container {
  margin-top: 30px;
  margin-bottom: 30px;
}

.headline {
  color: white;
  font-size: 1.3em;
  font-weight: bold;
}

.txt-full-white {
  color: white;
}

.uppercase {
  text-transform: uppercase;
}

.section-headline {
  color: @accent-color;
  display: inline-block;
  font-size: 1.2em;
  margin-left: 5px;
}

.section-content {
  margin-top: 10px;
  padding-left: 32px;
}

.section-content__item {
  display: block;
  margin-bottom: 10px;
}

.section-content__item-grid {
  flex: 1 1 0;

  margin-bottom: 10px;
  padding-right: 10px;
}

.section-content-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;

  margin-top: 10px;
  margin-bottom: 10px;
  padding-left: 32px;
}

.grid-item {
  padding-right: 20px;
}

.section-content__header {
  display: block;

  font-size: 1.1em;
  font-weight: 500;
}

.section-content__subheader {
  display: block;
  font-weight: 400;
}

.section-content__text {
  display: block;
  font-weight: 300;
}

.section-content__text--light {
  color: rgba(0,0,0,0.70);
  font-weight: 300;
}

.section-content__subheader,
.section-content__text--light,
.section-content__header {
  line-height: 1.5em;
}

.section {
  margin-top: 10px;
  margin-bottom: 10px;
}

.lang-icon {
  color: rgba(0,0,0,0.72);
  font-size: 3em;

  &:hover {
    color: @accent-color;
  }
}

.hobbies-container {
  margin-top: 30px;
}

.hobbies-content {
  display: flex;
  flex-direction: column;
}

.hobby-item {
  display: grid;
  grid-template-columns: 30px auto;

  color: rgba(255, 255, 255, .6);

  margin-right: 25px;
  margin-bottom: 10px;

  transition: .5s;

  &:hover {
    color: rgba(255, 255, 255, .8);
    transition: .5s;
  }
}

.hobby-item__icon {
  font-size: 1.3em;
}

.hobby-item__icon-label {
  top: 2.5px;
  position: relative;
}

.subheadline {
  color: rgba(255, 255, 255, .8);
  font-size: 1.2em;

  display: block;
  margin-bottom: 10px;
}

.squarred-grid-item {
  display: block;
  color: white;
  margin-left: 15px;
  padding-left: 10px;
}

.white-color{
  color: white;
}

.skills-content{
  padding-left: 0;
  justify-content: flex-start;
}
.without-margin{
  margin: 0;
}
</style>
