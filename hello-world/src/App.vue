<template>
  <div id="app">
    <span v-show='visible' style="font-family:Arial">A site where you click a button that constantly moves and you cant really click it</span>
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
  position: center;
}
span {
  width: 600px;
  height: 100px;
  text-align: center;
  font-size: large;
  position: absolute;
  transform: translate(-50%,-100%);
  left: 50%;
  top: 100%;
}

</style>
