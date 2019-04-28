<template>
  <div id="main">
    <div class="inputbox">
      <input type="text" v-model="search" placeholder="Search by name">
    </div>
    <div class="results" v-for="(person, index) in filteredPeople" v-bind:key="index">
      <h2>{{person.name}}</h2>
      <body>
        Company: {{person.company}}<br/>
        Email: {{person.email}}<br/>
        City: {{person.city}}<br/>
        Country: {{person.country}}<br/>
        {{person.job_history ? "Job History: " + person.job_history : ""}}
      </body>
    </div>
  </div>
</template>

<script>
import contacts from '../data/data.json';

contacts.forEach((contact) => {
  const stringifiedJobHistory = contact.job_history.join(', ');
  // eslint-disable-next-line
  contact.job_history = stringifiedJobHistory;
});

export default {
  name: 'Search',
  data() {
    return {
      search: '',
      people: contacts,
    };
  },
  computed: {
    filteredPeople() {
      const self = this;
      return this.people.filter(
        person =>
          person.name.toLowerCase().indexOf(self.search.toLowerCase()) >= 0,
      );
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.inputbox {
  margin: 20px;
}
.results {
    border: 1px solid black;
    max-width:50%;
    margin: auto;
}
</style>
