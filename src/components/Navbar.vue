<template>
  <div>
    <nav id="nav_header" class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <router-link to="/">
          <img :src="logo" width="32" :alt="alt" id="logo">
        </router-link>

        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <router-link class="nav-link active" to="/">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/pedidos">pedidos</router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "navbar",
  props: ["logo", "alt"]
}
</script>

<style scoped>
ul {
  display: flex;
  justify-content: end;
}

.navbar>.container-fluid {
  width: 90% !important;
}
.navbar-expand-lg .navbar-collapse{
  justify-content: flex-end !important;
  margin-right: 50px;
}
li {
  margin: auto;
}

.navbar-light .navbar-nav .nav-link{
  color: #929292 ;
}

.navbar-light .navbar-nav .nav-link.active {
  color: #e58d04;
}


.nav-link:hover {
  color: #e58d04 !important;
  cursor: pointer;
}

#nav_header {
  background: #222 !important;
  border-bottom: 4px solid #111;
}

</style>