<template>
  <div>
    <p> {{ y }} - &copy; copyhight</p>

  </div>
</template>

<script>

export default {
  name: "Footer",
  data() {
    return {
      y: null
    }
  }, methods: {
    //função que busca o ano atual
    async anoatual() {

      var currentTime = new Date();
      var y = currentTime.getFullYear()

      this.y = y;
    }
  },
  mounted() {
    // retornando a busca
    this.anoatual();
  }
}


</script>

<style scoped>
div, p {
  background: #444;
  margin-bottom: 0;
  height: 200px;
  text-align: center;
  align-items: center;
}

p {
  display: flex;
  margin: auto;
  justify-content: center;
  color: #e58d04;
}
</style>