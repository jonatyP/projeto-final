<template>
  <div class="app">
    <Home/>
  </div>
</template>

<script>
import Home from './components/main'

export default {
  name: 'app',
  components: {Home}, 
}
</script>

<style>
#scta { 
    width: 70%; 
    margin: 20px auto 0px auto;
    }
#cadastroLivro { 
    width: 40%; 
    margin: 20px auto 0px auto;
    }
#tblLivro{
   width: 65%; 
   margin: 20px auto 0px auto;
}
hr {
    border-color: #EE9056;
    border-style: solid none;
    border-width: 1px 0;
    margin: 18px 0;
}
.removido { 
    color: rgb(100, 2, 2); 
  }
  .removido label {
    text-decoration: line-through; 
  }   
ul li { 
    list-style-type: none; 
  }

</style>