<template>
  <div class="max-w-7xl mx-auto">
    <div class="container mx-auto px-6 pt-8">
      <h1 class="logo">Word Search</h1>
      <div class="flex flex-col justify-center items-center">
        <div class="flex justify-center ws-words"></div>
        <div class="flex justify-center overflow-scroll overscroll-contain relative">
          <section id="ws-area"></section>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      script: [
        {
          src: "/js/wordsearch.js",
          body: true
        },],}
      },
  data() {
    return {
      //words: ['one', 'two', 'three', 'four', 'five']
    }
  }
}
</script>
<style>
/*! purgecss start ignore */
/* .wrap {
  width: auto;
  margin: 0 auto;
  padding: 40px 0;
  text-align: center;
  position:relative;
} */
.logo, #gameArea {
  margin-bottom: 40px;
}
.ws-words {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 390px;
  width: 100%;
  list-style: none;
}
.ws-word {
  margin-bottom: 4px;
  padding: 0 0.5rem;
  font-size: 1.1rem;
}

.ws-words ::first-letter{
    text-transform : capitalize;
}
.ws-area {
  background: #fafafa;
  display: flex;
  padding: 20px;
  border-radius: 10px;
  -moz-user-select: -moz-none;
  -khtml-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
}
.ws-row {
  line-height: 0;
}
.ws-col {
  cursor: pointer;
}
.ws-col.ws-selected {
  background: #eee;
}
.ws-found {
  background: yellow;
}
.ws-game-over-outer {
  background: rgba(0, 0, 0, 0.85);
  height: 100%;
  left: 0;
  position: absolute;
  top: 0;
  width: 100%;
}
.ws-game-over-inner {
  width:100%;
  height:100%;
  padding:0;
  margin:0;
  display:table;
}
.ws-game-over {
  display:table-cell;
  vertical-align:middle;
}
.ws-game-over h2 {
  color:#FFFFFF;
  font-size:2em;
  text-transform:uppercase;
  padding:0;
  margin:0 0 9px 0;
}
.ws-game-over p {
  color:#FFFFFF;
  font-size:1em;
  padding:0;
  margin:0;
}
.cta_outline_white {
  max-width: 200px;
  padding: 0.4rem;
  color: white;
  border: 2px solid white;
}
@media screen and (min-width: 996px) {
  #ws-area {
    transform: scale(1);
  }
  .ws-words {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    max-width: 680px;
    width: 100%;
  }
}
/*! purgecss end ignore */
</style>