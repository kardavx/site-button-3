<template>
  <div id="app">
    <span id="misc"  v-show='visible' style="font-family:Arial">A WEBSITE WHERE YOU CLICK A BUTTON THAT CONSTANTLY MOVES AND YOU CANT REALLY CLICK IT</span>
    <span id="counter" v-show='!visible' :style="`font-family: ${ 'Arial' }; font-size: ${ GetSize }`">{{ GetCount }}</span>
    <Button @Hovered="HandleButHover()" @CountChanged="HandleCountChange($event)"></Button>
  </div>
</template>

<script>

import Button from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    Button,
  },
  created() {
    document.title = "cant click this"
  },
  data: () => ({
      visible: true,
      count: 0
  }),
  methods: {
    HandleButHover() {
      this.visible = false
    },
    HandleCountChange(CurrCount) {
      console.log("Count Change Parsed")
      localStorage.setItem("PlayerCount", CurrCount)
      this.count = CurrCount
      console.log(this.count)
    }
  },
  computed: {
    GetCount() {
      return this.count
    },
    GetSize() {
      if (this.count >= 1000) {
        return 38 + "vw"
      }
      return 45 + "vw"
    }
  }
}
</script>

<style>

#app {
  position: center;
}

#counter {
  text-align: center;
  white-space: nowrap;
  font-size: 45vw;
  opacity: 0.05;
  position: absolute;
  transform: translate(-50%,-50%);
  left: 50%;
  top: 50%;
  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none; /* Safari */
  -khtml-user-select: none; /* Konqueror HTML */
  -moz-user-select: none; /* Old versions of Firefox */
  -ms-user-select: none; /* Internet Explorer/Edge */
  user-select: none; /* Non-prefixed version, currently supported by Chrome, Edge, Opera and Firefox */
}

#misc {
  width: 600px;
  height: 100px;
  text-align: center;
  font-size: large;
  position: absolute;
  opacity: 0.5;
  transform: translate(-50%,-100%);
  left: 50%;
  top: 100%;
  -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none; /* Safari */
  -khtml-user-select: none; /* Konqueror HTML */
  -moz-user-select: none; /* Old versions of Firefox */
  -ms-user-select: none; /* Internet Explorer/Edge */
  user-select: none; /* Non-prefixed version, currently supported by Chrome, Edge, Opera and Firefox */
}

</style>
