<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { Ref, ref } from 'vue';
import data from '/Users/okadanatsuki/Development/Front End Mentor Practice/job-list-filter/data.json';
const jobData = data; 
</script>

<template>
  <main>
    <header>
      <svg width="1440" height="156" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path id="a" d="M0 0h1440v156H0z"/></defs><g fill="none" fill-rule="evenodd"><mask id="b" fill="#fff"><use xlink:href="#a"/></mask><use xlink:href="#a"/><g mask="url(#b)" fill="#63BABA"><path d="M495.73 563.419c-51.439-48.795-53.583-130.05-4.788-181.489a128.377 128.377 0 0 1 4.789-4.789l418.16-396.66c55.045-52.215 141.329-52.215 196.374 0 50.418 47.825 53.478 126.835 7.634 178.39l188.06-178.39c55.045-52.215 141.328-52.215 196.373 0 51.44 48.794 53.583 130.049 4.789 181.488a128.377 128.377 0 0 1-4.789 4.789l-418.158 396.658c-55.045 52.215-141.329 52.215-196.374 0-50.418-47.825-53.478-126.835-7.634-178.39L692.104 563.42c-55.045 52.215-141.328 52.215-196.373 0ZM360.464 45.523c-51.44-48.794-53.583-130.05-4.789-181.488a128.377 128.377 0 0 1 4.789-4.79l418.163-396.663c55.046-52.215 141.33-52.215 196.374 0 51.44 48.794 53.583 130.05 4.789 181.488a128.376 128.376 0 0 1-4.789 4.79L556.837 45.522c-55.045 52.215-141.328 52.215-196.373 0Zm-468.795 71.832c-51.439-48.795-53.583-130.05-4.789-181.489a128.377 128.377 0 0 1 4.79-4.788l418.16-396.661c55.045-52.215 141.328-52.215 196.373 0 51.44 48.794 53.583 130.05 4.79 181.488a128.378 128.378 0 0 1-4.79 4.789l-418.16 396.66c-55.045 52.216-141.329 52.216-196.374 0Z"/></g></g></svg> 
    </header>
      <!-- <div class="job-list"> -->
        <div class="job-list">
          <div v-for="job in jobData" :key="job.id" class="job-info">
            <img :src=" job.logo" alt="company's logo">
            <div class="flex-group">
              <div class="update-tag">
                <p>{{ job.company }}</p>
                <p class="new tag">NEW!</p>
                <p class="feture tag">FEATURED</p>
              </div>
              <h1 class="position">{{ job.position }}</h1>
              <div class="info-tags">
                <p>{{ job.postedAt }}</p>
                <p>{{ job.contract }}</p>
                <p>{{ job.location }}</p>
              </div>
            </div>
            <div class="filter-category">
              <p>{{ job.role }}</p>
              <p>{{ job.level }}</p>
              <p v-for="(language, index) in job.languages" :key="index">{{ language }}</p>
              <p v-for="(tool, index) in job.tools" :key="index">{{ tool }}</p>
            </div>
          </div>
        </div>
      <!-- </div> -->
  </main>
  
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=League+Spartan:wght@500;700&display=swap');

:root {
  --clr-primary-darkCyan:hsl(180, 29%, 50%);
  --clr-background-pghtCyan:hsl(180, 52%, 96%);
  --clr-position-darkCyan:hsl(180, 14%, 20%);
  --clr-category-darkGray:hsl(180, 8%, 52%);
  --clr-filterTablets-pghtCyan:hsl(180, 31%, 95%);

  --fs-body: 0.93rem;
  --fs-position: 1.1rem;
  --fw-bold: 700;
  --fw-regular: 500;
  --font-family: 'League Spartan', sans-serif;
}

main {
  font-family: var(--font-family);
  font-size: var(--fs-body);
  font-weight: var(--fw-bold);
  background-color: var(--clr-background-lightCyan);
  color: var(--clr-primary-darkCyan);
  
  display: grid;
  place-items: center;
}

header {
  background-color: var(--clr-primary-darkCyan);
}

.job-list {
  display: grid;  
  align-content: start;
  gap: 1.3rem;
  margin: 4rem;
  width: 1000px;
}

.job-info {
  display: flex;
  align-items: center;
  padding: 1.5rem;
  border-radius: 0.6rem;
  box-shadow: 0 5px 10px 5px rgb(213, 230, 229);
  background-color: white;
}

.flex-group {
  margin: 0 auto 0 20px;
}

.update-tag {
  display: flex;
}

.update-tag .tag {
  background-color: black;
  color: white;
  font-size: 0.8rem;
  border-radius: 1.5rem;
  padding: 3px 5px 0 5px;
  margin-left: 10px;
}

.update-tag .new {
  background-color: var(--clr-primary-darkCyan);
}

.position {
  font-size: var(--fs-position);
  color: var(--clr-position-darkCyan);
}

.info-tags {
  display: flex;
  color: var(--clr-category-darkGray);
  font-weight: var(--fw-regular);
}

.info-tags p{
  padding-right: 30px;
}

.filter-category {
  display: flex;
}

.filter-category p {
  background-color: var(--clr-background-pghtCyan);
  margin: 0 10px;
  padding: 8px;
}

/* 
@media (min-width: 600px) {
  main {
    min-height: 100vh;
    display: grid;
    place-items: center;
  }
} */

/* @media (min-width: 600px) {
  .job-item {
    border-radius: 3rem;
    box-shadow: .5rem 1rem 3rem;
}
} */

</style>
