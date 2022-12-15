<template>
  <section class="legend">
    <ul class="legend-list">
      <li class="category emotional">
        <p>Emotional</p>
      </li>
      <li class="category comedy">
        <p>Comedy</p>
      </li>
      <li class="category dance-fever">
        <p>Dance Fever</p>
      </li>
      <li class="category must-sees">
        <p>Must Sees</p>
      </li>
      <li class="category classics">
        <p>Classics</p>
      </li>
      <li class="category jukebox">
        <p>Jukebox</p>
      </li>
      <li class="category revolutionary">
        <p>Revolutionary</p>
      </li>
      <li class="category for-the-kids">
        <p>For the Kids</p>
      </li>
      <li class="category girl-power">
        <p>Girl Power</p>
      </li>
      <li class="category film-adaptations">
        <p>Film Adaptations</p>
      </li>
    </ul>
  </section>
</template>

<script>

export default {
  name: 'TableLegend'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/assets/variables.scss";
.legend {
  padding: 0;
  list-style: none;
  max-width: 800px;
  margin: auto;
  .legend-list {
    margin: auto;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    text-align: left;
    .category {
      margin-left: 40px;
      margin-right: 10px;
      margin: 0 10px 10px 40px;
      position: relative;
      &:before {
        position: absolute;
        content: '';
        height: 60px;
        width: 30px;
        left: -40px;
        top: 0;
        border: 1px solid $black;
      } 
      &.comedy:before {
        background-color: $blue-bright;
      } 
      &.dance-fever:before {
        background-color: $pink-med;
      } 
      &.classics:before {
        background-color: $gray;
      } 
      &.emotional:before {
        background-color: $blue-med;
      } 
      &.jukebox:before {
        background-color: $yellow;
      } 
      &.revolutionary:before {
        background-color: $green;
      } 
      &.girl-power:before {
        background-color: $pink;
      } 
      &.for-the-kids:before {
        background-color: $orange;
      } 
      &.film-adaptations:before {
        background-color: $blue;
      } 
      &.must-sees:before {
        background-color: $purple;
      } 
    }
  }
}

@media screen and (max-width: 992px){ 
  .legend {
   .legend-list {
    display: block;
    text-align: center;
    .category {
      display: inline-block;
      &:before {
        height: 40px;
      }
    }
   }
  }
}


</style>
