<template>
  <div class="pos">
    <el-row>
      <el-col :span="8" class="pp-order" id="order-list">
        <template>
          <el-tabs >
            <el-tab-pane label="点餐">
              <template>
                <el-table :data="tableData" border style="width: 100%" class="pp-table">
                  <el-table-column prop="goodsName" label="商品名称" align="center"></el-table-column>
                  <el-table-column prop="count" label="数量" align="center"></el-table-column>
                  <el-table-column prop="price" label="金额" align="center"></el-table-column>
                  <el-table-column fixed="right" label="操作" align="center" width="100">
                    <template slot-scope="scope">
                      <el-button @click="addOliderList(scope.row)" type="text" size="small">增加</el-button>
                      <el-button @click.native.prevent="deleteRow(scope.$index, tableData)" type="text" size="small">删除</el-button>
                    </template>
                  </el-table-column>
                </el-table>
              </template>
              <div class="pp-total-wrap">
                <small>数量：</small><span>{{totalCount}}</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
                <small>总计：</small><span>{{totalMoney}}</span> 元
              </div>
              <div class="pp-btn">
                <el-button type="warning">挂单</el-button>
                <el-button type="danger" @click="deleteAll()">删除</el-button>
                <el-button type="success" @click="checkOut()">结账</el-button>
              </div>
            </el-tab-pane>
            <el-tab-pane label="挂单">挂单</el-tab-pane>
            <el-tab-pane label="外卖">外卖</el-tab-pane>
          </el-tabs>
        </template>
        <template>
          <el-row>
            <el-col :span="10">
              接电话时
            </el-col>
            <el-col :sapn="14">
              <el-select v-model="form.value1" placeholder="请选择">
                <el-option
                  v-for="item in options"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value">
                </el-option>
              </el-select>
            </el-col>           
          </el-row>
          <el-row>
            <el-col :span="10">
              dmfvh
            </el-col>
            <el-col :sapn="14">
              <el-select v-model="form.value2" placeholder="请选择">
                <el-option
                  v-for="item in options"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value">
                </el-option>
              </el-select>
            </el-col>           
          </el-row>
          <el-row>
            <el-col :span="10">
              f 
            </el-col>
            <el-col :sapn="14">
              <el-select v-model="form.value3" placeholder="请选择">
                <el-option
                  v-for="item in options"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value">
                </el-option>
              </el-select>
            </el-col>           
          </el-row>
          <el-row>
            <el-col :span="10">
              xfb
            </el-col>
            <el-col :sapn="14">
              <el-select v-model="form.value4" placeholder="请选择">
                <el-option
                  v-for="item in options"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value">
                </el-option>
              </el-select>
            </el-col>           
          </el-row>
          <el-button type="danger" @click="clear">重置</el-button>
        </template>
      </el-col>
      <el-col :span="16">
        <div class="pp-shop-wrap">
          <div class="pp-shaop-title">常用商品</div>
          <div class="pp-shop-item">
            <ul class="clearfix">
              <li v-for="item in foodlist" :key="item.goodsId" @click="addOliderList(item)">
                <span>{{item.goodsName}}</span>
                <span class="pp-shop-price">¥{{item.price}}元</span>
              </li>
            </ul>
          </div>
        </div>
        <!-- <template>
          <div class="hello">
              <div v-for='item in showList'>{{item}}</div>
              <div @click="isActive = !isActive" class="show-more">{{word}}</div>
          </div>
        </template> -->
        <div class="pp-type">
          <template>
            <el-tabs>
              <el-tab-pane label="汉堡">
                <div>
                  <ul class="pp-cook-item clearfix">
                    <li class="pp-cook-list" v-for="item in often0Goods" :key="item.goodsId"  @click="addOliderList(item)">
                      <div class="pp-foodimg"><img :src="item.goodsImg" alt=""></div>
                      <div class="pp-food-detail">
                        <div class="pp-food-title">{{item.goodsName}}</div>
                        <div class="pp-food-price">¥{{item.price}}元</div>
                      </div>                      
                    </li>
                  </ul>
                </div>
              </el-tab-pane>
              <el-tab-pane label="小食">
                <div>
                  <ul class="pp-cook-item clearfix">
                    <li class="pp-cook-list" v-for="item in often1Goods" :key="item.goodsId"  @click="addOliderList(item)">
                      <div class="pp-foodimg"><img :src="item.goodsImg" alt=""></div>
                      <div class="pp-food-detail">
                        <div class="pp-food-title">{{item.goodsName}}</div>
                        <div class="pp-food-price">¥{{item.price}}元</div>
                      </div>                      
                    </li>
                  </ul>
                </div>
              </el-tab-pane>
              <el-tab-pane label="饮料">
                <div>
                  <ul class="pp-cook-item clearfix">
                    <li class="pp-cook-list" v-for="item in often2Goods" :key="item.goodsId"  @click="addOliderList(item)">
                      <div class="pp-foodimg"><img :src="item.goodsImg" alt=""></div>
                      <div class="pp-food-detail">
                        <div class="pp-food-title">{{item.goodsName}}</div>
                        <div class="pp-food-price">¥{{item.price}}元</div>
                      </div>                      
                    </li>
                  </ul>
                </div>
              </el-tab-pane>
              <el-tab-pane label="套餐">
                <div>
                  <ul class="pp-cook-item clearfix">
                    <li class="pp-cook-list" v-for="item in often3Goods" :key="item.goodsId"  @click="addOliderList(item)">
                      <div class="pp-foodimg"><img :src="item.goodsImg" alt=""></div>
                      <div class="pp-food-detail">
                        <div class="pp-food-title">{{item.goodsName}}</div>
                        <div class="pp-food-price">¥{{item.price}}元</div>
                      </div>                      
                    </li>
                  </ul>
                </div>
              </el-tab-pane>
            </el-tabs>
          </template>
        </div>
        <div class="wrap" v-for="item in toLearnList" :key="item.id" style="margin-bottom: 20px">
          <div>{{item.name}}</div>
          <List :item="item"></List>            
        </div>
      </el-col>
    </el-row>    
  </div>
</template>
<script>
import axios from 'axios'
import List from '@/components/page/list.vue'

export default {
  components: {
    List
  },
  data(){
    return {
      options: [{
          value: '选项1',
          label: '黄金糕'
        }, {
          value: '选项2',
          label: '双皮奶'
        }, {
          value: '选项3',
          label: '蚵仔煎'
        }, {
          value: '选项4',
          label: '龙须面'
        }, {
          value: '选项5',
          label: '北京烤鸭'
        }],
        form: {
          value1: '',
          value2: '',
          value3: '',
          value4: '',
        },       
      toLearnList:[{
        id: 1,
        name: 'html',
        age: 12,
        love: [
          {id: 1, name: '唱歌'},
          {id: 2, name: '跳舞'},
          {id: 3, name: '看书'},
          {id: 4, name: '下棋'},
          {id: 5, name: '旅游'},
        ]},
        {
          id: 2,
          name: 'vue',
          age: 5,
          love: [
            {id: 6, name: '唱歌'},
            {id: 7, name: '跳舞'},
            {id: 8, name: '看书'}
          ]},
        {
          id: 3,
          name: 'javascript',
          age: 10,
          love: [
            {id: 9, name: '唱歌'},
            {id: 10, name: '跳舞'}
          ]},
        {
          id: 4,
          name: 'jquery',
          age: 2,
          love: [
          {id: 11, name: '唱歌'}
        ]}
      ],
      tableData: [],
      totalCount: 0,
      totalMoney: 0,
      often0Goods: [],
      often1Goods: [],
      often2Goods: [],
      often3Goods: [],
      foodlist: [],
      // isActive:false,
    }
  },
  // computed:{
  //   word:function(){
  //     if(this.isActive == false){　　　　　　　　　　　//对文字进行处理
  //       return '展开'
  //     }else{
  //       return '收起'
  //     }
  //   }
  // },
  mounted() {
    var oredrHeight = document.body.clientHeight
    // console.log(oredrHeight);
    document.getElementById('order-list').style.height = oredrHeight + 'px'
    axios.get('https://www.easy-mock.com/mock/5b8b30dbf032f03c5e71de7f/kuaican/oftenGoods').then(res => {
      this.foodlist = res.data
      // console.log(res)
    }).catch(error => {
      alert('网络错误，不能访问')
    }),
    axios.get('https://www.easy-mock.com/mock/5b8b30dbf032f03c5e71de7f/kuaican/typeGoods').then(res => {     
      this.often0Goods = res.data[0]
      this.often1Goods = res.data[1]
      this.often2Goods = res.data[2]
      this.often3Goods = res.data[3]
    }).catch(error => {
      alert('网络错误，不能访问')
    })
  },
  methods: {
    // toggle() {
    //   this.isActive = !this.isActive;
    // },
    // 删除一行
    clear() {
      this.form.value1 = ''
      this.form.value2 = ''
      this.form.value3 = ''
      this.form.value4 = ''
    },
    deleteRow(index, rows) {
      this.$confirm('确认删除吗？')
        .then(_ => {
          rows.splice(index, 1)
          this.$message({
            showClose: true,
            message: '恭喜你，这是一条删除成功',
            type: 'success'
          })
        }).catch(_ => {});
      this.getMoney();
    },
    // 汇总数量和金额
    getMoney() {
      this.totalCount = 0
      this.totalMoney = 0
      if(this.tableData) {
        this.tableData.filter((item) => {
          this.totalCount += item.count
          this.totalMoney = this.totalMoney + (item.price*item.count)
        })
      }
    },
    addOliderList(item) {
      this.totalCount = 0
      this.totalMoney = 0
      //商品是否已存在于订单列表中
      let isHave = false
      for(let i=0; i<this.tableData.length; i++) {
        if(this.tableData[i].goodsId == item.goodsId) {
          isHave = true
        }
      }
      //根据判断的值编写业务逻辑
      if(isHave) {
        let arr = this.tableData.filter((o) => o.goodsId == item.goodsId)
        arr[0].count++
      } else {
        let newGoods = {
          goodsId: item.goodsId,
          goodsName: item.goodsName,
          price: item.price,
          count: 1
        }
        this.tableData.push(newGoods)
      }
      this.getMoney()
    },
    // 删除全部商品
    deleteAll() {
      this.tableData = []
      this.getMoney()
    },
    // 结账
    checkOut() {
      if (this.totalCount != 0) {
        this.tableData = []
        this.totalCount = 0
        this.totalMoney = 0
        this.$message({
          message: '恭喜你，结账成功！',
          type: 'success'
        })
      } else {
        this.$message({
          message: '请确认订单！',
          type: 'error'
        })
      }
    }
  }
}
</script>
<style lang="less" scoped>
li {
  list-style: none;
}
.pp-order {
  background-color: #f9fafc;
  border-right: 1px solid #c0ccda;
  height: 100%;
  padding: 20px;
}
.pp-btn {
  margin-top: 20px;
}
.pp-shop-wrap {
  .pp-shaop-title {
    height: 20px;
    border-bottom: 1px solid #d3dce6;
    background-color: #f9fafc;
    padding: 10px;
    text-align: left;
  }
  .pp-shop-item {
    li {
      float: left;
      border: 1px solid #e5e9f2;
      padding: 5px 10px;
      margin: 5px 10px;
      background-color: #fff;
      cursor: pointer;
      .pp-shop-price {
        color: #409EFF;
        margin-left: 5px;
      }
    }
  }
}
.pp-type {
  padding: 20px;
}
.pp-cook-list {
  padding: 10px 20px 10px 85px;
  border: 1px solid #e5e9f2;
  background-color: #fff;
  position: relative;
  height: 60px;
  float: left;
  margin-right: 20px;
  margin-bottom: 20px;
  cursor: pointer;
  .pp-foodimg {
    position: absolute;
    top: 50%;
    left: 10px;
    transform: translateY(-50%);
  }
  .pp-food-detail {
    .pp-food-price {
      margin-top: 10px;
      color: #fa5a4b;
    }
  }
}
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}
.pp-total-wrap {
  padding: 10px;
  border-bottom: 1px solid #ddd;
  span {
    color: #fa5a4b;
  }
}
</style>
<style lang="less">
.pp-table {
  .el-table thead {
    .el-table td, .el-table th {
      padding: 10px 0;
    }
  }
}
.el-table .warning-row {
    background: oldlace;
  }
  .el-table .success-row {
    background: #f0f9eb;
  }
.el-table td, .el-table th {
  padding: 5px 0;
}
</style>
