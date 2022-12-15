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
    this.elements = await this.getElements();
  },
  methods: {
    getElements: async () => {
      const query = `{
        elementCollection (order: number_ASC, limit: 200) {
          items {
            sys {
              id
            }
            name
            number
            abbreviation
            category
            startDate
            link
            active
            xPosition
            yPosition
            tonys
          }
        }
      }`;
      const fetchUrl = `https://graphql.contentful.com/content/v1/spaces/${process.env.VUE_APP_CONTENTFUL_SPACE_ID}`;
      const fetchOptions = {
        method: "POST",
        headers: {
          Authorization: `Bearer ${process.env.VUE_APP_CONTENTFUL_ACCESS_TOKEN}`,
          "Content-Type": "application/json"
        },
        body: JSON.stringify({ query })
      };

      try {
        const response = await fetch(fetchUrl, fetchOptions).then(response =>
          response.json()
        );
        return response.data.elementCollection.items;
      } catch (error) {
        throw new Error("Could not receive the data from Contentful!");
      }
    }
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
