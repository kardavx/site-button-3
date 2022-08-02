<template>
  <div>
    <button @mouseover='ButHover()'></button>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  methods: {
    ButHover() {
      let i = Math.floor(Math.random() * window.innerWidth) + 1;
      let j = Math.floor(Math.random() * window.innerHeight) + 1;
      this.style.left = i + "px";
      this.style.top = j + "px";
      this.$emit("Hovered")
    }
  },
  computed: {
    leftpos = function() {

    },
  }
}
</script>

<style scoped>

button {
  position: absolute;
  width: 400px;
  height: 200px;
  transform: translate(-50%,-50%);
  left: 50%;
  top: 50%;
}

</style>
