<template>
  <div>
     <section id="job-details" :details="details">
        <h2>Job Details</h2>
        <h4>{{details.title}}</h4>
        <p>{{details.description}}</p>
      </section>
  </div>
</template>

<script>
export default {
  name: 'JobDetails',
  data() {
    return {
      apiUrl: '../static/listing.json',
      details: []
    };
  },
  mounted() {
    this.getJobDetails();
  },
  methods: {
    getJobDetails() {
      fetch(this.apiUrl)
        .then(response => response.json())
        .then(response => (this.details = response));
    }
  }
};
</script>

<style scoped>
h2 {
  font-size: 1.5rem;
  font-weight: bold;
}

section {
  grid-column: 2/3;
}
</style>
