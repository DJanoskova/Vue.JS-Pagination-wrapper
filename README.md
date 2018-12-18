# Vue.JS-Pagination-wrapper
A pagination wrapper for element-ui containing paging logic. You can extend the Pagination.vue file based on your needs.

## Simple usage example
```
<template>
  <div>
    <Pagination :source="source"
      v-model="paginatedData"
      :pageSize="3"/>
      
    <img v-for="image in paginatedData"
      :key="image.id"
      :src="image.src">
  </div>
</template>

<script>
import Pagination from './Pagination'

export default {
  data () {
    return {
      source: [
        {id: 1, src: 'image1.jpg'},
        {id: 2, src: 'image2.jpg'},
        {id: 3, src: 'image3.jpg'},
        {id: 4, src: 'image4.jpg'},
        {id: 5, src: 'image5.jpg'}
      ],
      paginatedData: []
    }
  },
  components: {
    Pagination
  }
}
</script>
```
