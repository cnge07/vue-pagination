<template>
  <nav v-if="page > 1">
	  <ul class="pagination">
	  	<li><a href="javascript:;" v-if="current > 1" v-on:click="current =1"> 首页 </a></li>
	  	<li><a href="javascript:;" v-if="current > 1" v-on:click="--current"> 上一页 </a></li>
	  	<li v-for="n in page" v-bind:class="{ 'active': n + 1 == current }"><a href="javascript:;" v-on:click="current = n + 1"> {{ n + 1 }} </a></li>
		<li><a href="javascript:;" v-if="current < page" v-on:click="++current"> 下一页</a></li>
		<li><a href="javascript:;" v-if="current < page" v-on:click="current = page"> 尾页 </a></li>		
	  </ul>
	  <ul class="pagination pull-right">
	  	<li><span> 共 {{ total }} 条数据 </span></li>
	    <li><span> 每页 {{ display }} 条数据 </span></li>
	    <li><span> 共 {{ page }} 页 </span></li>
	    <li><span> 当前第 {{ current }} 页 </span></li>
	  </ul>
	</nav>
</template>
<script>
export default {
    props: {
        total: {
            type: Number,
            default: 0
        },
        display: {
            type: Number,
            default: 3
        },
        current: {
            type: Number,
            default: 1
        }
    },
    computed: {
        page() {
            return Math.ceil(this.total / this.display);
        }
    }
}
</script>
