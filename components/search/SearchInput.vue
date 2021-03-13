<template>
  <form @submit.prevent="search">
    <div class="search-bar">
      <SearchIcon />

      <input
        ref="search"
        type="text"
        placeholder="Search..."
        @keyup="keyupEventHandler"
      />
    </div>
  </form>
</template>

<script>
import SearchIcon from '@/assets/icons/search.svg'

export default {
  components: {
    SearchIcon,
  },
  data() {
    return {
      timeout: null,
    }
  },
  methods: {
    async search() {
      const query = this.$refs.search.value

      const result = await this.$content('articles').search(query).fetch()

      console.log(result)
    },
    keyupEventHandler(e) {
      if (this.timeout !== null) {
        clearTimeout(this.timeout)
        this.timeout = null
      }

      e.preventDefault()
      this.timeout = setTimeout(() => {
        this.search()
      }, 500)
    },
  },
}
</script>

<style lang="scss" scoped>
.search-bar {
  display: flex;
  width: 100%;
  margin: 36px 0 24px;
  padding-bottom: 6px;
  border-bottom: 2px solid #fff;
  color: #fff;
}

svg {
  width: 45px;
  height: 45px;
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
</style>
