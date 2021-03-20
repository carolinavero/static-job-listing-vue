<template>
    <div class="jobs">
      <div class="job-list">

        <div v-if="activeFilters" class="filter">

          <div v-for="filter in filters" :key="filter.id">
            {{ filter }}
          </div>

          <div class="card">
            <div class="filtersList">

              <div class="filterTag">
                <span>nome</span> 
                <button @click="removeFilter"><img src="../assets/icon-remove.svg" alt="remove"></button> 
              </div>
            
            </div>

            <div>
              <button @click="clearFilters" class="clearLink">
                Clear
              </button>
            </div>

          </div>

        </div>

        <Card 
          v-for="job in jobs" 
          :key="job.id" 
          :id="job.id"
          :logo="job.logo"
          :company="job.company" 
          :newTag="job.new"
          :featuredTag="job.featured"
          :position="job.position"
          :role="job.role"
          :level="job.level"
          :postedAt="job.postedAt"
          :contract="job.contract"
          :location="job.location"
          :languages="job.languages"
          :tools="job.tools"
        />
      </div>
    </div>
</template>

<script>

import Card from '../components/Card'

export default {
  name: 'JobList',
  data() {
    return {
      jobs: [],
      activeFilters: false
    }
  },
  components: {
    Card,
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const res = await fetch("data.json");
      const values = await res.json();
      console.log(values)
      this.jobs = values;
      return values;
    },
    removeFilter() {
      console.log("remove this filter");
    },
    clearFilters() {
      console.log('filter')
      activeFilters = false;
    }
  }
}
</script>

<style scoped>

.jobs {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.job-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  max-width: 1440px;
  width: 100%;

  margin-bottom: 4rem;
}

.filter {
  display: flex;
  width: 80%;

}
.filtersList {
  display: flex;
  flex-direction: row;
}

.filterTag {
  background-color: var(--lightGrayishCyanBg);
  color: var(--desaturatedDarkCyan);
  font-size: .85rem;
  font-weight: bold;

  border-radius: .5rem;
  margin: 5px;
  position: relative;

  display: flex;
  justify-content: space-between;
  align-items: center;
}
.filterTag span {
  padding: 7px 10px;
}
.filterTag button {
  background-color: var(--desaturatedDarkCyan);
  /* position: absolute; */
  top: 0;
  right: 0;
  bottom: 0;
  border-top-right-radius: .5rem;
  border-bottom-right-radius: .5rem;
  padding: 7px;
}
.filterTag button img {
  width: 15px;
}

.filterTag button:hover {
  background-color: var(--veryDarkGrayishCyan);
}

.clearLink {
  color: var(--desaturatedDarkCyan);
  font-size: .85rem;
  font-weight: bold;
  background-color: #fff;
}

.clearLink:hover {
  text-decoration: underline;
}

</style>