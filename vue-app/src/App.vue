<template>
  <div class="navbar navbar-expand-lg navbar-light bg-light">
            <div class="collapse navbar-collapse">
                    <li class="navbar-nav">
                           <router-link  class="nav-item nav-link active" to="/">Home</router-link> 
                    </li> 
                    <li class="navbar-nav">
                        <router-link class="nav-item nav-link active" to="/about">About</router-link>
                    </li> 
            </div>
  </div>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


@import'~bootstrap/dist/css/bootstrap.css'
</style>
