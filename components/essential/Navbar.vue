<template>
  <header class="navbar">
    <div class="navbar-section">
      <Link to="/" label="Bloxt" />
    </div>
    <div class="navbar-section">
      <Link to="/blog" label="Blog" />
    </div>
  </header>
</template>

<style lang="scss" scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 56px;

  &-section {
    display: flex;
  }
}
</style>
