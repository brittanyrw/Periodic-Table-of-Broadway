<template>
  <section class="about-section">
    <h1>About the data</h1>
    <div class="about-content">
      <div class="key">
        <p>Key</p>
        <div class="example">
          <p class="number">#</p>
          <div class="link">
            <span>Wiki</span>
            <img
                class="link-arrow"
                :alt="arrow"
                :src="require(`../assets/arrow.svg`)"
              />
          </div>
          <p class="abbreviation">Abbreviation</p>
          <p class="name">Show Name</p>
          <p class="date">Opening Date</p>
          <p class="tonys"># Tony Awards</p>
        </div>
      </div>
      <ol class="about-list">
        <li>The shows above were performed either on Broadway, Off-Broadway or both in New York City.</li>
        <li>The Tony Awards number is a summation of all awards every Broadway production of the show including revivals. </li>
        <li>The year listed is the opening date of the first Broadway or Off-Broadway production.</li>
        <li>Created by <a href="https://musicalwebdev.com" target="_blank">Brittany Walker</a> using Vue.js and <a href="https://www.contentful.com" target="_blank">Contentful</a>.</li>
      </ol>
    </div>
  </section>
</template>

<script>

export default {
  name: 'AboutSection',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/assets/variables.scss";

.about-section {
  background-color: $pink;
  border: 1px solid $black;
  margin: auto;
  max-width: 800px;
  padding: 20px;
  h1 {
    margin: 0;
  }
  a {
    color: $black;
    font-weight: bold;
  }
  .about-content {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    .example {
      border: 1px solid $black;
      position: relative;
      width: 200px;
      height: 200px;
      display: flex;
      flex-wrap: wrap;
      flex-direction: column;
      justify-content: center;
      .number {
        position: absolute;
        top: -5px;
        left: 10px;
      }
      .link {
        position: absolute;
        top: 0;
        right: 0;
        .link-arrow {
          height: 25px;
          width: 25px;
          transform: rotate(90deg);
        }
      }
      .abbreviation {
        font-weight: bold;
        font-size: 1.6em;
        margin: 0;
      }
      .name {
        margin: 0;
        font-size: 1em;
      }
      .date {
        margin: 0;
        font-size: .7em;
      }
      .tonys {
        position: absolute;
        right: 0;
        bottom: -16px;
        border-top: 1px solid $black;
        border-left: 1px solid $black;
        padding: 2px 5px;
      }
    }
    .about-list {
      text-align: left;
      margin: 20px; 
    }
  }
}

@media screen and (max-width: 992px) {
  .about-section {
    .about-content {
      display: block;
      text-align: center;
      .example {
        margin: auto;
      }
    }
  }
}

</style>
