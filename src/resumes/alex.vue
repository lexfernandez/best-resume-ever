<template>
  <div class="resume" id="resume2">
    <div class="right-column">
      <div>
        <div class="headline align-text-center">
          <span> {{ person.name.first }} {{ person.name.middle }} {{ person.name.last }} </span>
        </div>
        <div class="align-text-center">
          <a :href="contactLinks.email">
            <div class="block-marged txt-full-white contact">
              <i class="fa fa-envelope contact-icon"></i>
              <span class="block-marged txt-full-white">
                {{ person.contact.email }}
              </span>
            </div>
          </a>

          <div class="block-marged txt-full-white contact">
            <i class="fa fa-phone contact-icon"></i>
              <span class="block-marged txt-full-white">
                {{ person.contact.phone }}
              </span>
          </div>

          <a v-if="person.contact.github" :href="contactLinks.github" >
            <div class="block-marged txt-full-white contact">
              <i class="fa fa-github contact-icon"></i>
              <span class="block-marged txt-full-white">
                {{ person.contact.github }}
              </span>
            </div>
            
          </a>
        </div>
      </div>
      <div class="experience-section section">
        <div class="icon">
          <i class="material-icons small-icon">work</i>
          <span class="section-headline">{{ lang.experience }}</span>
        </div>

        <div class="section-content">
          <a
            v-for="(experience, index) in person.experience"
            :key="index"
            class="section-content__item"
            :href="experience.website"
          >
          <div>
            <span class="experience-position">{{ experience.position }}</span> 
            <span v-if="experience.company" class='experience-company'>@ {{ experience.company }}</span>
            <span v-if="experience.timeperiod" style="float:right" class='experience-timeperiod'>{{ experience.timeperiod }}</span>
          </div>

          <div
              v-for="(achievement, index) in experience.achievements"
              :key="index" style="padding-left:15px;">
              <div class="icon">
                <i class="fa fa-circle bullet"></i>
                <span class="achievement">{{ achievement.description }}</span>
              </div>
            </div>
            <span class="section-content__text--light">{{ experience.description }}</span>
          </a>
        </div>
      </div>

      <div v-if="person.projects" class="projects-section section">
        <div class="icon">
          <i class="material-icons">code</i>
          <span class="section-headline">{{ lang.projects }}</span>
        </div>

        <div class="section-content">
          <a
            v-for="(project, index) in person.projects"
            :key="index"
            class="section-content__item"
            :href="project.url"
          >
            <span class="section-content__header">{{ project.name }}</span>
            <span class="section-content__subheader">{{ project.platform }}</span>
            <span class="section-content__text">{{ project.description }}</span>
            <span class="section-content__text--light">{{ project.url }}</span>
          </a>
        </div>
      </div>

      <div class="education-section section">
        <div class="icon">
          <i class="material-icons">school</i>
          <span class="section-headline">{{ lang.education }}</span>
        </div>

        <div class="section-content">
          <a
            v-for="(education, index) in person.education"
            :key="index"
            class="section-content__item"
            :href="education.website"
          >
            <span class="section-content__header">{{ education.school }}</span>
            <span class="section-content__subheader">{{ education.degree }}</span>
            <span class="section-content__text">{{ education.timeperiod }}</span>
            <span class="section-content__text--light">{{ education.description }}</span>
          </a>
        </div>
      </div>

      <div v-if="person.contributions" class="contributions-section section">
        <div class="icon">
          <i class="fa fa-heart font-awesome-icons"></i>
          <span class="section-headline">{{lang.contributions}}</span>
        </div>

        <div class="section-content-grid">
          <a
            v-for="(contribution, index) in person.contributions"
            :key="index"
            :href="contribution.url"
            class="section-content__item-grid"
          >
            <span class="section-content__header">{{ contribution.name }}</span>
            <span class="section-content__text">{{ contribution.description }}</span>
            <span
              class="section-content__text--light"
              style="word-break: break-all;"
            >{{ contribution.url }}</span>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'alex';

export default Vue.component(name, getVueOptions(name));
</script>

<style lang="less" scoped>
@accent-color: #34495e;

.resume {
  display: flex;
  position: relative;

  font-family: "Roboto" !important;
  font-size: 0.9em;
}

.right-column {
  display: flex;
  flex-direction: column;
  padding: 30px;

  height: 100%;
  width: 100%;
}

a {
  color: inherit;
  cursor: pointer;
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

.contact {
  display: inline-table
}

.bullet {
  font-size: 10px;
  padding-right: 5px;
}

.contact-icon {
  color: @accent-color;
  font-size: 1.5em;
  margin-left: 10px;

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
  color: @accent-color;
  font-size: 1.3em;
  font-weight: bold;
}

.txt-full-white {
  color: @accent-color;
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

.align-text-center {
  text-align: center;
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

.experience-position {
  display: inline;

  font-size: 1em;
  font-weight: 500;
}

.experience-company {
  font-size: .9em;
  // font-weight: 500;
}

.experience-timeperiod {
  font-size: .9em;
  // text-align: right
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
  color: rgba(0, 0, 0, 0.7);
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

.achievement {
  font-size: 14px;
}
.lang-icon {
  color: rgba(0, 0, 0, 0.72);
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

  color: rgba(255, 255, 255, 0.6);

  margin-right: 25px;
  margin-bottom: 10px;

  transition: 0.5s;

  &:hover {
    color: rgba(255, 255, 255, 0.8);
    transition: 0.5s;
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
  color: rgba(255, 255, 255, 0.8);
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

.white-color {
  color: white;
}

.skills-content {
  padding-left: 0;
  justify-content: flex-start;
}
.without-margin {
  margin: 0;
}
</style>
