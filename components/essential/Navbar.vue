<template>
  <header :class="scrollClass">
    <div class="navbar">
      <div class="navbar-section">
        <Link to="/" label="Bloxt" variant="navbar-brand" />
      </div>
      <div class="navbar-section">
        <Link to="/blog" label="Blog" variant="navbar-link" />
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      scrollClass: '',
    }
  },
  beforeMount() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll(event) {
      if (window.scrollY > 5) {
        this.scrollClass = 'scrolled'
      } else {
        this.scrollClass = ''
      }
    },
  },
}
</script>

<style lang="scss" scoped>
@import '~assets/styles/palette.scss';
header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 10;
  height: 56px;
  display: flex;
  transition: all 0.5s;

  .navbar {
    width: 1600px;
    margin: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;

    &-section {
      display: flex;
    }
  }
  &.scrolled {
    background-color: $cardBackground;
    box-shadow: 0 0.03rem 0.5rem rgb(100, 100, 100);
  }
}
</style>
