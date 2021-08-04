<template>
  <div class="app-container">
    
    <div class="layout-content">
      <keep-alive v-if="$route.meta.keepAlive">
        <router-view></router-view>
      </keep-alive>
      <router-view v-else></router-view>
    </div>

    
    <div class="layout-footer">
      <TabBar :data="tabbars" @change="handleChange" />
    </div>
  </div>
</template>

<script>
import TabBar from '@/components/TabBar'


export default {
  name: 'AppLayout',
  data() {
    return {
      tabbars: [
        {
          title: '基础信息',
          to: {
            name: 'Home'
          },
          icon: 'home-o'
        },
        {
          title: '身份证件',
          to: {
            name: 'About'
          },
          icon: 'user-o'
        },
        {
          title: '签署协议',
          to: {
            name: 'Home'
          },
          icon: 'user-o'
        }
      ]
    }
  },
  components: {
    TabBar
    
  },
  methods: {
    handleChange(v) {
      console.log('tab value:', v)
    }
  }
}
</script>
