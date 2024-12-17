<script setup>
import { reactive, ref } from 'vue'

const router = useRouter()
const route = useRoute()
const active = ref('Demo')
const tabbarData = reactive([
  {
    icon: 'wap-home-o',
    title: '列表',
    icon: 'i-carbon-text-align-justify',
    to: {
      name: 'Demo',
    },
  },
  {
    icon: 'gem-o',
    title: 'Api',
    icon: 'i-carbon-api',
    to: {
      name: 'Tools',
    },
  },
  {
    icon: 'user-o',
    title: '表单',
    icon: 'i-carbon-data-format',
    to: {
      name: 'Playground',
    },
  },
  {
    icon: 'user-o',
    title: '个人中心',
    icon: 'i-carbon-user-identification',
    to: {
      name: 'About',
    },
  },
])
function onTabChange(name) {
  const tabNames = ['Demo', 'Tools', 'Playground', 'About']
  active.value = name
  const index = tabNames.indexOf(name)
  const routeName = tabNames[index]
  router.replace({ name: routeName })
}
</script>

<template>
  <van-tabbar v-model="active" :placeholder="true" fixed @change="onTabChange">
    <van-tabbar-item
v-for="(item) in tabbarData" :key="item.to.name" :icon="item.icon" :title="item.to.name"
      :name="item.to.name"
>
      {{ item.title }}
      <template #icon>
        <div :class="item.icon" />
      </template>
    </van-tabbar-item>
  </van-tabbar>
</template>
