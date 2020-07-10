<template>
  <div class="navbar navbar-default topnav">
    <div class="container">
      <div class="navbar-header">
         <button type="button" class="navbar-toggle" @click="toggleNav">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <router-link to="/" class="navbar-brand">
          <span class="title">
          <img :src="logo.src" :alt="logo.title">
           {{ logo.title }}</span>
        </router-link>
        </div>
        <div id="top-navbar-collapse" :class="['collapse', 'navbar-collapse', { in: showCollapsedNav }]">
        <ul class="nav navbar-nav">
          <li v-for="(item, index) in navList" :class="{ active: index === activeNavIndex }" :key="item">
            <a href="#" @click="changeNavIndex(index)">{{ item }}</a>
          </li>
        </ul>
         <!-- 入口组件 -->
          <div class="navbar-right">
            <!-- 搜索框 -->
            <SearchInput/>
            <TheEntry/>
          </div>
      </div>
      </div>
    </div>
</template>

<script>
// 引入 TheEntry.vue 的默认值
import TheEntry from '@/components/layouts/TheEntry'
// 引入 SearchInput.vue 默认值
import SearchInput from '@/components/layouts/SearchInput'
export default {
  name: 'TheHeader',
  // 添加 components 选项，并注册 TheEntry
   components: {
    TheEntry,
     // 注册 SearchInput
    SearchInput
  },
  data() {
    return {
      logo: {
        src: `${this.uploadsUrl}png/vue.png!/both/40x40`,
        title: 'VuejsCaff'
      },
      navList: ['社区', '头条', '问答', '教程'],
      activeNavIndex: 0,
      showCollapsedNav: false
    }
  },
  beforeCreate() {
    this.uploadsUrl = 'https://yp.dayanyu.com.cn/images/'
  },
  methods: {
    changeNavIndex(index) {
      this.activeNavIndex = index
    },
    toggleNav() {
      this.showCollapsedNav = !this.showCollapsedNav
    }
  }
}
</script>

<style scoped>
.title{
  color:black;
}
.navbar-default .navbar-nav > .active > a { background: rgba(0,0,0,.03);}
</style>

