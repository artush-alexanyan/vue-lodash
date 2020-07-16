<template>
  <div id="app">
    <div id="nav">
      <div class="container-fluid mt-3">
        <nav aria-label="breadcrumb">
          <ol class="breadcrumb">
            <router-link to="/" tag="li" class="breadcrumb-item">Home</router-link>
            <router-link to="/about" tag="li" class="breadcrumb-item">About</router-link>
            <router-link to="/test" tag="li" class="breadcrumb-item">Test</router-link>
          </ol>
        </nav>        
      </div>
    </div>
    <router-view/>
  </div>
</template>

<style>
#nav li.router-link-exact-active {
  color: red;
  cursor: pointer;
}
#nav li{
  cursor: pointer;
}
</style>
