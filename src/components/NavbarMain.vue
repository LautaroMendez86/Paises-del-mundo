<template>
  <nav class="nav">
    <h2 class="h2">Paises del mundo</h2>
  </nav>
</template>

<script>
export default {
  name: "NavbarMain",
};
</script>

<style>
.nav {
  display: flex;
  align-items: center;
  height: 90px;
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.964);
  box-shadow: 0px 0px 10px 10px rgba(34, 34, 34, 0.081);
}

.h2 {
  margin: 15px;
  margin-left: 50px;
}
</style>
