<template lang="html">
<div class="content">
    <img src="../assets/quirkietimes-hero.jpg" alt="Quirkie Time Header">
  <div class="maintenance">
    <h1>Coming soon</h1>
    <h2>The Quirkie Times</h2>
  </div>
</div>
</template>
<script>
export default {
mounted: function () {
  console.log(this.$route.path)
}
}
</script>
<style>
/*! purgecss start ignore */
body, html {
  height: 100%;
  width: 100%;
  font-size: 1em;
}
.maintenance h1 {
  font-size: 190%;
  color: #fff;
  text-shadow: -2px 2px 3px rgba(0,0,0,0.5);
  color: #d6336c;
  text-align: center;
}
.maintenance {
  /* width: 200px; */
  height: 200px;
  position: absolute;
  left: 50%;
  top: 50%;
  margin-left: -100px;
  fill: #d6336c;
}
.content {
  height: 100%;
  width: 100%;
  background-color: #5471B9;
}
/*! purgecss end ignore */
</style>