<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { Ref, ref } from 'vue';
import data from '/Users/okadanatsuki/Development/Front End Mentor Practice/job-list-filter/data.json';
const jobData = data; 
</script>

<template>
  <main>
    <div class="main">

      <div class="main__list">

        <div v-for="job in jobData" :key="job.id" class="flex-group">
          <img :src=" job.logo" alt="company's logo">
          <div class="main__items">

            <div class="labels">
              <h1 class="company">{{ job.company }}</h1>
              <p class="new-label">NEW!</p>
              <p class="feture-label">FEATURED</p>
            </div>

            <h2 class="position">{{ job.position }}</h2>
            
            <div class="category">
              <p class="posted">{{ job.postedAt }}</p>
              <p class="contract">{{ job.contract }}</p>
              <p class="location">{{ job.location }}</p>
            </div>

          </div>

          <div class="main__tags">{{ job.languages }}</div>

        </div>

      </div>
    </div>
  </main>
  
</template>

<style>
.flex-group {
  display: flex;
}

.labels {
  display: flex;
}

.category {
  display: flex;
}

.main__tags {
  display: flex;
}

</style>
