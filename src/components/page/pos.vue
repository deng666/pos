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
                      <el-button @click="handleClick(scope.row)" type="text" size="small">增加</el-button>
                      <el-button @click.native.prevent="deleteRow(scope.$index, tableData)" type="text" size="small">删除</el-button>
                    </template>
                  </el-table-column>
                </el-table>
              </template>
              <div class="pp-btn">
                <el-button type="warning">挂单</el-button>
                <el-button type="danger">删除</el-button>
                <el-button type="success">结账</el-button>
              </div>
            </el-tab-pane>
            <el-tab-pane label="挂单">挂单</el-tab-pane>
            <el-tab-pane label="外卖">外卖</el-tab-pane>
          </el-tabs>

        </template>
      </el-col>
      <el-col :span="16">
        <div class="pp-shop-wrap">
          <div class="pp-shaop-title">常用商品</div>
          <div class="pp-shop-item">
            <ul class="clearfix">
              <li v-for="item in oftenGoods">
                <span>{{item.goodsName}}</span>
                <span class="pp-shop-price">¥{{item.price}}元</span>
              </li>
            </ul>
          </div>
        </div>
        <div class="pp-type">
          <template>
            <el-tabs>
              <el-tab-pane label="汉堡">
                <div>
                  <ul class="pp-cook-item clearfix">
                    <li class="pp-cook-list" v-for="item in foodlist">
                      <div class="pp-foodimg"><img :src="item.img" alt=""></div>
                      <div class="pp-food-detail">
                        <div class="pp-food-title">{{item.foodName}}</div>
                        <div class="pp-food-price">¥{{item.price}}元</div>
                      </div>                      
                    </li>
                  </ul>
                </div>
              </el-tab-pane>
              <el-tab-pane label="小食">小食</el-tab-pane>
              <el-tab-pane label="饮料">饮料</el-tab-pane>
              <el-tab-pane label="套餐">套餐</el-tab-pane>
            </el-tabs>
          </template>
        </div>
      </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
  data(){
    return {
      tableData: [{
        goodsName: '火锅',
        count: '1',
        price: '25'
      }, {
        goodsName: '猪蹄',
        count: '1',
        price: '30'
      }, {
        goodsName: '臭豆腐',
        count: '1',
        price: '35'
      }, {
        goodsName: '棉花糖',
        count: '2',
        price: '22'
      }],
      oftenGoods: [
        {
          goodsId: 1,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 2,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 3,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 4,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 5,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 6,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 7,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 8,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 9,
          goodsName: '香辣鸡腿堡',
          price: 18
        },
        {
          goodsId: 10,
          goodsName: '香辣鸡腿堡',
          price: 18
        }
      ],
      foodlist: [
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        },
        {
          foodId: 1,
          foodName: '香辣鸡腿堡',
          price: 18,
          img: 'static/img/hamburger.png'
        }
      ]
    }
  },
  mounted:function(){
    var oredrHeight = document.body.clientHeight
    // console.log(oredrHeight);
    document.getElementById('order-list').style.height = oredrHeight + 'px'
  },
  methods: {
    handleClick(row) {
      console.log(row);
    },
    deleteRow(index, rows) {
      rows.splice(index, 1);
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
