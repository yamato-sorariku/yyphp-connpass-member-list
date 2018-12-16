<template>
  <div>
    <vs-navbar 
      class="nabarx">
      <vs-navbar-title>
        <img 
          class="title-icon"
          src="yyphp_logo.png" 
          @click="$router.push('/')">
      </vs-navbar-title>

      <vs-navbar-item index="0">
        <vs-button 
          :href="'https://yyphp.connpass.com'"
          target 
          color="success" 
          type="filled">YYPHP CONNPASS</vs-button>
      </vs-navbar-item>

    </vs-navbar>
    <nuxt/>
  </div>
</template>

<style src="material-icons/iconfont/material-icons.css">
</style>

<style>
.title-icon {
  height: 5rem;
}
</style>
