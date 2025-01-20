<template>
  <div class="periodic-table-wrapper">
    <section>
      <ul class="table">
        <li class="table-legend">
          <TableLegend />
        </li>
        <li 
          v-for="show in shows" 
          :key="show.sys.id" 
          class="show"
          :class="slug(show.category[0])"
          :style="`grid-column: ${show.xPosition}; grid-row: ${show.yPosition};`"
        >
          <a :href="show.link" target="_blank" class="show-link">
            <img
                :alt="`Link to ${show.name} website`"
                :src="require(`../assets/arrow.svg`)"
              />
          </a>
          <p class="number">{{ show.number }}</p>
          <p class="abbreviation">{{ show.abbreviation }}</p>
          <p 
            class="show-name"
            :class="[{ shrink: show.name.length > 18 }]"
          >
            {{ show.name }}
          </p>
          <p class="date">{{ new Date(show.startDate).toLocaleDateString('en-us', { year:"numeric"}) }}</p>
          <p class="check" v-if="show.seen">
            <img alt="check icon" :src="require(`../assets/check.svg`)"
              />
          </p>
          <p class="tonys" v-if="show.tonys">{{ show.tonys }}</p>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>

import TableLegend from './TableLegend.vue'

export default {
  name: 'PeriodicTable',
  props: {
    shows: Array
  },
  components: {
    TableLegend
  },
  methods: {
    slug(title) {
      return title.toLowerCase()
        .replace(/ /g, "-")
        .replace(/ /g, ":")
        .replace(/ /g, "'")
        .replace(/[^\w-]+/g, "");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/assets/variables.scss";

* {
  box-sizing: border-box;
}

ul {
  padding: 0;
  list-style: none;
}

li {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

p {
  margin: 0;
  font-size: .8em;
}

.periodic-table-wrapper {
  margin-bottom: 50px;
}

.table {
  display: grid;
  grid-template-columns: repeat(18, 1fr);
  grid-template-rows: repeat(10, 1fr);
  max-width: 1400px;
  margin: auto;
}

.show {
  border: 1px solid $black;
  height: 120px;
  width: 75px;
  overflow: hidden;
  position: relative;
  padding: 2px;
  margin: 1px;
  transition: .5s ease-out;
  cursor: pointer;
}

.show:hover {
  transform: scale(2);
  z-index: 99;
  transition: .5s ease-in;
}

.show-link {
  height: 25px;
  width: 25px;
  position: absolute;
  right: 0px;
  top: -2px;
  transform: rotate(90deg);
}

.show-link:hover {
  transform: translateX(2px) translateY(-2px) rotate(90deg);
  transition: .5s ease-in-out;
}

.tonys {
  position: absolute;
  right: 0;
  bottom: 0;
  border-top: 1px solid $black;
  border-left: 1px solid $black;
  padding: 2px 5px;
}

.check img {
  height: 20px;
  position: absolute;
  left: 3px;
  bottom: 3px;
}

.emotional {
  background-color: $blue-med;
}

.comedy {
  background-color: $blue-bright;
}
.dance-fever {
  background-color: $pink-med;
}

.must-sees {
  background-color: $purple;
}

.classics {
  background-color: $gray;
}

.jukebox {
  background-color: $yellow;
}

.revolutionary {
  background-color: $green;
}

.film-adaptations {
  background-color: $blue;
}

.for-the-kids {
  background-color: $orange;
}

.girl-power {
  background-color: $pink;
}

.number {
  position: absolute;
  top: 1px;
  left: 3px;
}

.shrink {
  font-size: .5em;
}
.date {
  font-size: .5em;
}

.abbreviation {
  font-size: 35px;
  font-weight: bold;
}

.table-legend {
  grid-area: 1/4/3/12;
}

@media screen and (max-width: 992px){
  .table {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    .table-legend {
      order: -10;
      width: 100%;
      margin-bottom: 20px;
    }
    .show {
      width: 150px;
      height: 150px;
      p {
        font-size: 1em;
      }
      .date {
        font-size: .8em;
      }
      .abbreviation {
        font-size: 2em;
      }
      &:hover {
        transform: scale(1);
      }
      &.emotional {
        order: -9;
      }
      &.comedy {
        order: -8;
      }
      &.dance-fever {
        order: -7;
      }
      &.must-sees {
        order: -6;
      }
      &.classics {
        order: -5;
      }
      &.jukebox {
        order: -4;
      }
      &.revolutionary {
        order: -3;
      }
      &.for-the-kids {
        order: -2;
      }
      &.girl-power {
        order: -1;
      }
      &.film-adaptations {
        order: 0;
      }
    }
  }
}
</style>

