<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div :style="{width: pageType==='normal' ? '200px' : '100px'}" class="sidebar">
    <template v-for="(item,index) in list" :key="index">
      <router-link :to="rootUrl + '/' + item.url"
                   class="choice-item"
      >{{ item.title }}
      </router-link>
    </template>
    <div class="triangle1"></div>
    <div v-if="pageType==='normal'" class="triangle2"></div>
  </div>
</template>

<script>
import store from "@/store"

export default {
	props: {
		list: Array,
		rootUrl: String
	},
	data() {
		return {}
	},
	methods: {},
	computed: {
		pageType() {
			return store.state.page.pageType
		}
	}
}
</script>

<style lang="less" scoped>
a {
  display: block;
  color: black;
  text-align: center;
  line-height: 40px;
  height: 40px;
  font-weight: 400;
  font-size: 15px;
  text-decoration: none;
}

.router-link-active {
  font-weight: 700;
  font-size: 18px;
}

.sidebar {
  position: relative;
  width: 200px;
  height: 400px;
  padding-top: 50px;
  box-sizing: border-box;
  margin-top: 20px;
  background-color: rgb(135, 213, 236);
}

.triangle1 {
  position: absolute;
  width: 1px;
  height: 0px;
  left: -50px;
  top: 60px;
  border: 25px solid transparent;
  border-right-color: rgb(135, 213, 236);
}

.triangle2 {
  position: absolute;
  width: 0px;
  height: 0px;
  bottom: 0;
  border: 100px solid transparent;
  border-left-color: rgb(33, 111, 135);
  border-bottom-color: rgb(33, 111, 135);
}


</style>