<template>
  <div>
    <p>{{ y }} - &copy; copyhight</p>

  </div>
</template>

<script>

export default {
  name: "Footer",
  data() {
    return {
      y: '2021'
    }
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