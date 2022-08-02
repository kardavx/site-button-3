<template>
  <div id="app">
    <span v-show='visible'>A site where you click a button that constantly moves and you cant really click it</span>
    <Button @Hovered="HandleButHover()"></Button>
  </div>
</template>

<script>

import Button from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    Button
  },
  data: () => ({
      visible: true
  }),
  methods: {
    HandleButHover() {
      this.visible = false
    }
  }
}
</script>

<style>
#app {
  position: absolute;
  transform: translate(-50%,-50%);
  left: 50%;
  top: 50%;
}
span {
  width: 600px;
  height: 100px;
  text-align: center;
  font-family: "Monaco", Monospaced;
  position: absolute;
  transform: translate(-50%,-200%);
  left: 50%;
  top: 200%;
}
html,
body {
  margin: 0;
  padding: 0;
  background-color:rgb(79, 79, 79);
}
</style>
