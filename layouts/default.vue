<template>
  <div class="container">
    <Navbar />
    <div class="content-wrapper">
      <Nuxt />
    </div>
    <Footer />
  </div>
</template>

<style lang="scss">
body {
  margin: 0;
  .container {
    width: 1600px;
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    .content-wrapper {
      width: 1240px;
      margin: 20px auto;
    }
  }
}
</style>
