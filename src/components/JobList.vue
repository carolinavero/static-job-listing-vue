<template>
    <div class="jobs">
      <div class="job-list">
        <Card 
          v-for="job in jobs" 
          :key="job.id" 
          :logo="job.logo"
          :company="job.company" 
          :newTag="job.new"
          :featuredTag="job.featured"
          :position="job.position"
          :role="job.role"
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
// @ is an alias to /src
import Card from '../components/Card'

export default {
  name: 'JobList',
  data() {
    return {
      jobs: [],
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
}

</style>