# vue-pagination


```html
<template>
 <p> 当前页码 ： {{ current }} -- 每页 ：<select v-model="display"><option v-for="n in 20" value="{{ n + 1 }}">{{ n + 1 }}</option></select> 条数据 </p>
<pagination v-bind:total="total" v-bind:display.sync="display" v-bind:current.sync="current"></pagination>
</template>
```

```javascript
import pagination from './src/pagination'
export default {
  components: {
    pagination    
  },
  data () {
    return {
      total : 15,
      display: 10,
      current : 1
    }
  },
  watch:{
    display:function(val){
      this.display = parseInt(val,10);
    },
    current :function(val ,oldval){
      console.log(val,oldval);
    }
  }
}
```
