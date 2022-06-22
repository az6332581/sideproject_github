<template>
  <div class="container">
    <SearchList/>
    <ShowList/>
  </div>
</template>

<script>
  import SearchList from './components/SearchList'
  import ShowList from './components/ShowList'

  export default {
    name: 'App',
    components: {
      SearchList,
      ShowList
    },
  }
</script>
