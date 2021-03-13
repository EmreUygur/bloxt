<template>
  <div class="search">
    <button type="button" class="search-button">
      <SearchIcon @click="isActive = true" />
    </button>

    <div class="search-panel" :class="{ active: isActive }">
      <div class="search-wrapper">
        <SearchInput />
      </div>
    </div>
  </div>
</template>

<script>
import SearchIcon from '@/assets/icons/search.svg'

export default {
  components: {
    SearchIcon,
  },
  data() {
    return {
      isActive: false,
    }
  },
}
</script>

<style lang="scss" scoped>
.search {
  display: inline-block;
  &-button {
    background-color: transparent;
    display: flex;
    align-items: center;
    width: 36px;
    height: 36px;
    border-radius: 50%;
    margin: 0;
    padding: 0;
    border: none;
    outline: none;
    cursor: pointer;
    transition: box-shadow 0.25s ease-out;

    svg {
      width: auto;
      height: 60%;
      margin: auto;
    }

    &:hover {
      box-shadow: 0 1px 6px rgba(32, 33, 36, 0.28);
    }
  }

  &-panel {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    color: #fff;
    background-color: #000;
    z-index: 100;

    &.active {
      display: flex;
    }
  }

  &-wrapper {
    width: 1600px;
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    font-size: 36px;
    line-height: 40px;
    margin: 0 auto;
  }
}
</style>
