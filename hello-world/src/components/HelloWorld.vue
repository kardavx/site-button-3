<template>
  <div>
    <button :style="`top: ${ GetTop }; left: ${ GetLeft }; transform: ${ GetVisible }`" @click='ClickHandler()' @mouseover='TimeOutHandler()'></button>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data() {
    return {
      top: "50%",
      left: "50%",
      visible: true,
      count: 0,
      Timeout: null
    }
},
  created() {
    const Storage = localStorage.getItem("PlayerCount")
    if (Storage) {
      this.count = Storage
      this.$emit("CountChanged", Storage)
    }
  },
  methods: {
    TimeOutHandler() {
      if (this.Timeout != null) {
        return
      }
      const RandomTime = Math.floor((Math.random() * 5) - 1)
      this.Timeout = setTimeout(this.ButHover, RandomTime * 100);
    },
    ClickHandler() {
      this.count++
      this.$emit("CountChanged", this.count)
      this.ButHover()
    },
    ButHover() {
      console.log("got hover info")
      if (this.Timeout != null) {
        clearTimeout(this.Timeout);
        this.Timeout = null
      }
      console.log("hover");
      const RandomX = (Math.floor(Math.random() * window.innerWidth) / 1.2) + "px"
      const RandomY = (Math.floor(Math.random() * window.innerHeight) / 1.2) + "px"
      this.left = RandomX
      this.top = RandomY
      this.visible = false
      console.log(this.left)
      console.log(this.top)
      this.$emit("Hovered")
    },
  },
  computed: {
    GetTop() {
        return this.top
    },
    GetLeft() {
        return this.left
    },
    GetVisible() {
      if (!this.visible) {
        return "translate(0%,0%)"
      } else return "translate(-50%, -50%)"
    }
  }
}
</script>

<style scoped>

button {
  position: absolute;
  width: 200px;
  height: 100px;
  background-color: #e7e7e7; color: black;
  border-radius: 8px;
  border-color: aliceblue;
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
  transform: translate(-50%, -50%);
  left: 50%;
  top: 50%;
}
</style>