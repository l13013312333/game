<template>
  <div>
    <el-container id="container">
      <el-header id="header">
        <el-button type="warning"
                   icon="el-icon-menu"
                   plain
                   @click="drawer = true" />
      </el-header>
      <el-main id="main">
        <slot></slot>
      </el-main>
    </el-container>
    <el-drawer :visible.sync="drawer"
               direction="ltr"
               size="60%">
      <el-menu :default-active="activeIndex"
               class="el-menu-vertical-demo"
               background-color="#545c64"
               text-color="#fff"
               active-text-color="#ffd04b">
        <el-menu-item v-for="menu in menuConfig"
                      :key="menu.index"
                      :index="menu.index">
          <span slot="title"
                @click="$emit('changeVal', menu.index)">{{ menu.name }}</span>
        </el-menu-item>
      </el-menu>
    </el-drawer>
  </div>
</template>

<script>
module.exports = {
  props: ['activiyName', 'menuConfig'],
  data() {
    return {
      drawer: false,
      activeIndex: this.activiyName
    }
  }
}
</script>

<style>
#container {
  width: 100%;
  max-height: -webkit-fill-available;
}

#header {
  line-height: 60px;
  background: yellowgreen;
}

#main {
  background: #ffffffc7;
  height: 100vh;
}
/** 滾動Bar */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1; 
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: #888; 
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555; 
}
</style>