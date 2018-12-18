<template>
  <ElPagination
    :layout="layout"
    :page-size="pageSize"
    :total="source.length"
    :background="background"
    :currentPage="page"
    @current-change="currentChange"/>
</template>

<script>
import { Pagination } from 'element-ui'

export default {
  props: {
    value: {
      type: Array
    },
    source: {
      type: Array
    },
    pageSize: {
      type: Number,
      default: 20
    },
    currentPage: {
      type: Number,
      default: 1
    },
    layout: {
      type: String,
      default: 'prev, pager, next'
    },
    background: {
      type: String | Boolean,
      default: false
    },
    small: {
      type: String | Boolean,
      default: false
    }
  },
  data () {
    return {
      page: this.currentPage || 1
    }
  },
  methods: {
    currentChange (page) {
      this.page = page
    },
    reset () {
      this.page = 1
    }
  },
  computed: {
    displayedData () {
      const offset = (this.page - 1) * this.pageSize
      const clonedSource = JSON.parse(JSON.stringify(this.source))
      return clonedSource.splice(offset, this.pageSize)
    }
  },
  watch: {
    displayedData () {
      this.$emit('input', this.displayedData)
    },
    page () {
      this.$emit('curentChange', this.page)
    }
  },
  components: {
    [Pagination.name]: Pagination
  }
}
</script>
