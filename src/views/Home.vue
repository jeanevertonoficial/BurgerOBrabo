<template>
  <Banner/>
  <div class="main-container">
    <h1>Monte o seu Burger</h1>
    <BurgerForm/>
  </div>
</template>

<script>
import Banner from "@/components/Banner";
import BurgerForm from "@/components/BurgerForm";
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Home",
  components: {Banner, BurgerForm}
}
</script>

<style scoped>

</style>