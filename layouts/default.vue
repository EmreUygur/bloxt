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
@import '~assets/styles/palette.scss';
body {
  margin: 0;
  background-color: $background;
  .container {
    width: 1600px;
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    .content-wrapper {
      width: 1240px;
      margin: (56px + 20px) auto 20px auto;
    }
  }
}
</style>
