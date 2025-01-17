<template>
  <header>
    <h1>Periodic Table of Broadway</h1>
    <p>A table showing a list of popular Broadway and Off-Broadway shows.</p>
  </header>
  <PeriodicTable :shows="elements"/>
  <AboutSection />
</template>

<script>
import PeriodicTable from './components/PeriodicTable.vue'
import AboutSection from './components/AboutSection.vue'
import data from './data/data.json';


export default {
  name: 'App',
  components: {
    PeriodicTable,
    AboutSection
  },
  data() {
    return {
      elements: []
    }
  },
  async created() {
    this.elements = data.data.elementCollection.items;
  }

}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
