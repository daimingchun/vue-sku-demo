<template>
  <div class="hello product-sku">
    <div class="sku-item" v-for="(value, key, topIndex) in initSkuData">
      <h3 class="sku-title">{{key}}</h3>
      <div class="sku-list">
        <template v-for="item in value">
          <el-checkbox :label="item.name" :true-label="item.name" v-model="item.value" :key="item.name" @change="checkboxChangeHandle(item, topIndex)"></el-checkbox>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      skuResults:{},
      selectedSku:[],
      initSkuData: {
      '颜色':[
        {group: '颜色', name: '红色', value: '', id: 111},
        {group: '颜色', name: '黄色', value: '', id: 122},
        {group: '颜色', name: '蓝色', value: '', id: 133}
      ],
      '尺寸':[
        {group: '尺寸', name: 'M', value: '', id: 211},
        {group: '尺寸', name: 'L', value: '', id: 222},
        {group: '尺寸', name: 'XL', value: '', id: 233}
        ],
      '性别':[
        {group: '性别', name: '男', value: '', id: 311},
        {group: '性别', name: '女', value: '', id: 322},
        {group: '性别', name: '人妖', value: '', id: 333}
        ]
      },
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    checkboxChangeHandle(item, index){
      this.selectedSkuhandle(item, index)
    },
    selectedSkuhandle (options, index){
      if(options.value) { //根据被选的值，判断是否被选中
        this.addSelectedSku(options, index)
      }else {
        this.delSelectedSku(options, index)
      }
    },
    //增加用户所选SKU数据
    addSelectedSku(options, index){
      let selectedSku = this.selectedSku
      if(!selectedSku[index]) {
        selectedSku[index] = []
      }
      selectedSku[index].push(options)
      console.log('增加已选',selectedSku)
    },
    //删除用户所选的SKU数据
    delSelectedSku(options, index){
      let selectedSku = this.selectedSku
      for(let i=0;i<selectedSku[index].length; i++) {
        let curSku = selectedSku[index][i]
        if(curSku.id == options.id) {
          selectedSku[index].splice(i, 1)
        }
      }
      console.log('删除已选',selectedSku)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
