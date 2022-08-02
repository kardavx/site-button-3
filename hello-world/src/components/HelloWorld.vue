<template>
  <div>
    <button :style="`top: ${ GetTop }; left: ${ GetLeft }; transform: ${GetVisible ? 'translate(-50%, -50%)' : 'translate(0%,0%)'}`" @mouseover='ButHover()'></button>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data() {
    return {
      top: "50%",
      left: "50%",
      visible: true
    }
},
  methods: {
    ButHover() {
      console.log("hover");

      const RandomX = (Math.floor(Math.random() * window.innerWidth) / 1.2) + "px"
      const RandomY = (Math.floor(Math.random() * window.innerHeight) / 1.2) + "px"
      this.left = RandomX
      this.top = RandomY
      this.visible = false
      console.log(this.left)
      console.log(this.top)
      this.$emit("Hovered")
    }
  },
  computed: {
    GetTop() {
        return this.top
    },
    GetLeft() {
        return this.left
    },
    GetVisible() {
      console.log(this.visible)

      console.log(this.visible ? 'translate(50%,-50%)' : 'translate(0%,0%)' )
      return this.visible
    }
  }
}
</script>

<style scoped>

button {
  position: absolute;
  width: 200px;
  height: 100px;
  transform: translate(-50%, -50%);
  left: 50%;
  top: 50%;
}
</style>
