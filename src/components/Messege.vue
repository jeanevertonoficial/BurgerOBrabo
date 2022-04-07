<template>
  <div class="messege-container">
    <p>{{ msg }}</p>
  </div>
</template>

<script>
export default {
  name: "Messege",
  props: {
    msg: String
  }
}
</script>

<style scoped>
.messege-container {
  color: #004085;
  background: #cce5ff;
  border: 2px solid #88DAff;
  border-radius: 5px;

  max-width: 400px;
  margin: 20px auto;
  text-align: center;
}
p{
  padding: 10px;
  margin: inherit;
  padding: 0;
}
</style>