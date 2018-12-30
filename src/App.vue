<template>
  <div id="app">
  
  <!--   <HelloWorld/> -->
    <Table2/>
    <table3/>
  </div>
</template>

<script>
/* import HelloWorld from './components/HelloWorld' */
import Table2 from './components/table2'
import table3 from './components/table3'
export default {
  name: 'App',
  components: {
    /* HelloWorld, */
    Table2,
    table3
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
