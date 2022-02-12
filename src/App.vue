<template>
  <h1 class="mt-3">DPI & Pixel Converter</h1>

  <div id="nav">
    <router-link to="/" class="btn btn-outline-primary me-5">Home</router-link>
    <a href="https://sdwh.dev" class="btn btn-outline-primary">sdwh.dev</a>
  </div>

  <router-view/>
</template>

<style lang="scss">
@import '~bootstrap/dist/css/bootstrap.css';
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Noto+Sans+TC:wght@400;500;700&display=swap');

#app {
  font-family: 'Inter', 'Noto Sans TC', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 1rem 0 1rem;
  padding: 10px;
}

#nav {
  padding: 20px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &:hover {
      color: #eaeaea;
    }

    &.router-link-exact-active {
      background-color: var(--bs-blue);
      color: #eaeaea;
    }
  }
}
</style>
