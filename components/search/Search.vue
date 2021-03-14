<template>
  <div class="search">
    <button type="button" class="search-button">
      <SearchIcon @click="isActive = true" />
    </button>

    <div class="search-panel" :class="{ active: isActive }">
      <div class="search-container">
        <div class="search-container-bar">
          <SearchIcon />
          <input
            ref="searchInput"
            type="text"
            placeholder="Search..."
            @keyup="keyupEventHandler"
          />
          <CloseIcon @click="isActive = false" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchIcon from '@/assets/icons/search.svg'
import CloseIcon from '@/assets/icons/x.svg'

export default {
  components: {
    SearchIcon,
    CloseIcon,
  },
  data() {
    return {
      isActive: false,
      timeout: null,
    }
  },
  methods: {
    async search() {
      const query = this.$refs.searchInput.value

      const result = await this.$content('articles').search(query).fetch()

      console.log(result)
    },
    keyupEventHandler() {
      if (this.timeout !== null) {
        clearTimeout(this.timeout)
        this.timeout = null
      }

      this.timeout = setTimeout(() => {
        this.search()
      }, 500)
    },
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

  &-container {
    width: 1600px;
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    font-size: 36px;
    line-height: 40px;
    margin: 0 auto;

    &-bar {
      display: flex;
      width: 100%;
      margin: 36px 0 24px;
      padding-bottom: 6px;
      border-bottom: 2px solid #fff;
      color: #fff;

      svg {
        width: 45px;
        height: 45px;
        &:last-child {
          cursor: pointer;
        }
      }

      input {
        flex-grow: 1;
        background-color: transparent;
        font-size: 36px;
        margin: 0 6px;
        color: inherit;
        border: none;
        outline: none;
      }
    }
  }
}
</style>
