<template>
  <div class="banner-style">
    <h1>Burger O Brabo</h1>
  </div>
</template>

<script>
export default {
  name: "Banner"
}
</script>

<style scoped>
.banner-style {
  /*background: url('https://static.onecms.io/wp-content/uploads/sites/9/2018/11/burger-king-whopper-shopper-FT-BLOG1118.jpg') 0 -250px;*/
  background: url('/public/img/burger.jpg') 0 -250px;
  background-size: cover;
  background-repeat: no-repeat;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  backdrop-filter: drop-shadow(4px 4px 10px #3d3d3d);

}
h1 {

  font-size: 60px;
  font-weight: 700;
  text-transform: uppercase;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: auto;
  padding: 10px 20px;
  height: 100px;
  background: #e58d04;
  border: 1px solid rgba(19, 19, 19, 0.17);
  box-shadow: 5px 5px 10px rgba(105, 91, 91, 0.35);
}

@media screen and (max-width: 600px) {
  h1 {
    font-size: 32px;
    width: 100%;
  }
  .banner-style {
    align-items: flex-start;
    justify-content: flex-start;
    height: 400px;
    background-size: contain;
    width: auto;
    background: url('/public/img/burger.jpg') -1362px -496px;
   /* background: url('https://static.onecms.io/wp-content/uploads/sites/9/2018/11/burger-king-whopper-shopper-FT-BLOG1118.jpg') -50px -450px;*/
  }
}
</style>