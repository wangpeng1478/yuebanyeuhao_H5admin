<style lang="less">
 .house{
   padding-top: 77px;
  .selectsNmae{
    .ivu-select-not-found{
      display:none
    }
   }
  .input-group {
    position: relative;
    display: table;
    border-collapse: separate;
    input{
        box-sizing: border-box;
        border: solid 1px #ddd;
        font-size: 12px;
        height: 31px;
        line-height: 1.42857;
        padding: 4px;
        border-right: none;
        text-align: center;
        width:35%;
        color: #495060;
    }
    input:focus{
      border-color: #57a3f3;
      outline: 0;
      box-shadow: 0 0 0 2px rgba(45,140,240,.2);
    }
    input:first-child{
      border-radius: 3px 0 0 3px;
    }
    span{
      display: inline-block;
      width: 30%;
      height: 31px;
      line-height: 31px;
      text-align: center;
      background-color: #eee;
      border: 1px solid #ccc;
      font-size: 12px;
      vertical-align: top;
      border-radius: 0 3px 3px 0;
    }
  }
  .ivu-card{
    margin-bottom:5px;
  }
  .padd10{
    .ivu-card-body{
      padding:5px;
    }
  }
  .titims{
    .ivu-card-body{
      padding:7px;
      .lesr{
        float: left;
      }
      .rigths{
        float:right;
        line-height: 33px;
        padding-right: 10px;
      }
    }
  }
  .lstable{
    .tableUl{
      .ls{margin-bottom:10px;}
      .li{
        background:#e6f5ff;
        padding: 10px;
        border:1px solid #c1e7ff;
        .le{
          float:left;
          cursor: pointer;
          &:hover{
            opacity: 0.7;
          }
        }
        .rig{
          float:right;
          a{
            margin: 0 10px;
          }
        }
      }
    }
  }
  .pages{
     float: right;
     margin: 15px 5px 5px 0;
     padding-bottom:30px;
   }
   .ovhidese{
     overflow:auto;
     .tablese{
       min-width: 1300px;
     }
   }

 }
.house{
  .selectUI{
    width: 100%;
    height: 32px;
    line-height: 1.5;
    padding: 4px 7px;
    font-size: 12px;
    border: 1px solid #dddee1;
    border-radius: 4px;
    color: #495060;
    background-color: #fff;
  }
  .sou1{
    background:#fff;
    padding: 4px;
  }
  .sou2{
    background:#fff;
    padding: 4px;
    box-shadow: 1px 2px 1px 0px rgba(0, 0, 0, 0.13);
    .soup{
      text-align:center;
      padding: 5px 0;
      .ivu-icon{
        padding-left: 5px;
      }
    }
    .on{
      color:#2b85e4;
    }
  }
 .navfix{
    position:fixed;
    top:40px;
    left:0;
    width:100%;
    z-index: 10;
    .cons{
      background:#fff;
      height:100vh;
      overflow: hidden;
      .botonbur{
        position:fixed;
        bottom:0;
        left:0;
        width:100%;
        button{
          width:50%;
        }
        .ivu-btn-ghost{background:#fff}
      }
      .p1{
        text-align: center;
        padding: 10px 0;
        border-bottom: 1px solid #eee;
        border-right: 1px solid #eee;    
        &:first-child{
         border-top: 1px solid #eee;
        }
      }
      .p2{
        text-align: center;
        padding: 10px 0;
        border-bottom: 1px solid #eee;   
        &:first-child{
         border-top: 1px solid #eee;
        }
      }
      .on{
        background: #f7f7f7;
      }
      .on2{
        color:#2b85e4;
      }
    }
    .ovhide{
      height:80vh;
      overflow:auto;
      padding-bottom: 50px;
    }
 }
}
 .hide{
   height:50vh;
   overflow:hidden;
 }
 .house{
  .listmap{
    border-bottom: 1px solid #eee;
    margin-bottom: 8px;
    padding-bottom: 8px;
    padding-left: 6px;
    position: relative;
    p{
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      font-size: 12px;
      margin-bottom: 2px;
    }
    .ivu-tag{
      padding: 0 2px;
      font-size: 11px;
      height: 20px;
      line-height: 20px;
      margin:0;
      zoom: 0.8;
      // font-weight: 100;
      vertical-align: text-top;
    }
    .bl{
      font-size:15px;
      font-weight: 600;
    }
    .ribot{
      position: absolute;
      right: 0;
      bottom: 0;
      .ivu-btn{
        padding:5px;
        margin: 3px;
      }
    }
  }
  .cardlistno{
    background: #fff;
    margin: 5px 0;
    padding: 40px;
    text-align: center;
    i{
      font-size: 2em;
      margin-bottom: 10px;
    }

  }
 }
</style>

<template>
   <div class="house cf" :class="{hide:ovhide}">
    <pre>{{HouseTableData}}</pre>
   <!--  <Card class='sere'> -->
      
    <Form :model="screens" :label-width="70">
        <div class="navfix">
          <Row class="sou1">
          <Col>
            <Select 
              v-model="screens.name" 
              class="selectsNmae" 
              filterable
              clearable
              remote
              :remote-method="remoteMethod"
              :placeholder = "sesongs"
              @on-change = "changseee2"
              :loading="loadingse">
                <Option v-for="(option, index) in optionsName" :value="option.value" :key="index">{{option.label}}</Option>
            </Select>
          </Col>
        </Row>
          <Row class="sou2">
            <Col span="6"><p @click="navsr(0)" :class="{on:onst==0}" class="soup">所在区域<Icon type="arrow-down-b"></Icon></p></Col>
            <Col span="6"><p @click="navsr(1)" :class="{on:onst==1}" class="soup">跟进类型<Icon type="arrow-down-b"></Icon></p></Col>
            <Col span="6"><p @click="navsr(2)" :class="{on:onst==2}" class="soup">归属人<Icon type="arrow-down-b"></Icon></p></Col>
            <Col span="6"><p @click="navsr(3)" :class="{on:onst==3}" class="soup">筛选<Icon type="funnel"></Icon></Icon></p></Col>
         </Row>
         <Row class="cons" v-if="onst==0">
          <Col span="8" class="ovhide">
            <p class="p1" :class="{on:yeson==index}" v-for="(item,index) in region" :key="item.value" @click="clickyes(index,item.value)">{{item.value}}</p>
          </Col>
          <Col span="16" class="ovhide" style="background: #f7f7f7;">
            <p class="p2" :class="{on2:yeson2==index}" v-for="(item,index) in childrenre" :key="item.value" @click="clickyes2(index,item.value)">
              {{item.value}}
            </p>
          </Col>
          <ButtonGroup class="botonbur">
            <Button type="ghost" icon="reply" @click="conno">重置</Button>
            <Button type="primary" icon="ios-search" @click="conyes">确认</Button>
          </ButtonGroup>
       </Row>
      <Row v-if="onst==1" class="cons">
      <Col class="ovhide">
        <p class="p2" :class="{on:yeson3== -1}" @click="clickyes4">全部</p>
        <p class="p2" :class="{on:yeson3==index}" v-for="(item,index) in gentype" :key="item.value" @click="clickyes3(index,item.value)">{{item.value}}</p>
      </Col>
    </Row>
    <Row v-if="onst==2" class="cons">
      <Col class="ovhide">
        <p class="p2" :class="{on:yeson4== -1}" @click="clickyes5">全部</p>
        <p class="p2" :class="{on:yeson4==index}" v-for="(item,index) in cityList" :key="item.value" @click="clickyes6(index,item.value)">{{item.value}}</p>
      </Col>
    </Row>

      <Row v-if="onst==3" class="cons" style="padding: 5px 10px 0 10px;border-top: 1px solid #eee;">
        <Col class="ovhide">
              <FormItem label="最近地铁">
                 <select v-model="screens.metro" class="selectUI">
                    <option v-for="item in metros" :value="item.value" :key="item.value">{{ item.label }}</option>
                 </select>
              </FormItem>
              <FormItem label="装修情况">
                   <select v-model="screens.Renovation" class="selectUI">
                      <option v-for="item in zhuangxtype" :value="item.value" :key="item.value">{{ item.label }}</option>
                   </select>
                </FormItem>
                 <FormItem label="租金区间">

              <div class="input-group">
                <input v-model="screens.rent.min" type="text" maxlength="8">
                <input v-model="screens.rent.max" type="text" maxlength="8">
                <span>元</span>
              </div>

              </FormItem>
               <FormItem label="面积区间">
                <div class="input-group">
                  <input v-model="screens.minaji.min" type="text" maxlength="8">
                  <input v-model="screens.minaji.max" type="text" maxlength="8">
                  <span>m²</span>
                </div>
              </FormItem>
               <FormItem label="出售单价">
              <div class="input-group">
                <input v-model="screens.zongshojia.min" type="text" maxlength="8">
                <input v-model="screens.zongshojia.max" type="text" maxlength="8">
                <span>元</span>
              </div>
              </FormItem>
              <FormItem label="业主类型">
                  <Cascader :data="identitydata" v-model="screens.identity" change-on-select></Cascader>
              </FormItem>
              <FormItem label="ID">
                 <Input v-model="screens.id"></Input>
              </FormItem>
               <FormItem label="是否上架">
                  <RadioGroup v-model="screens.yesNO" type="button">
                      <Radio label="上架"></Radio>
                      <Radio label="下架"></Radio>
                  </RadioGroup>
              </FormItem>
              <FormItem label="是否有图">
                  <RadioGroup v-model="screens.yesNOimg" type="button">
                      <Radio label="有图"></Radio>
                      <Radio label="无图"></Radio>
                  </RadioGroup>
              </FormItem>
        </Col>
        <ButtonGroup class="botonbur">
          <Button type="ghost" icon="reply" @click='reson'>重置</Button>
          <Button type="primary" icon="ios-search" @click='screenss'>确认</Button>
        </ButtonGroup>
      </Row>


        </div>


    </Form>


       <Card class='titims'>
      <div class="cf">
      <Button class="lesr" type="primary" @click.prevent="addLOUPan" shape="circle" icon="ios-plus-outline">添加房源</Button>
       <div class="rigths">房源数量：<b>{{totals}} </b>套</div>
     </div>
    </Card>

   <Card class="padd10">
      <div v-for="(item, index) in HouseTableData" :key="index" class="listmap">
         <p class="bl">{{item.name}} <Tag v-if="item.imgyesNO" type="border" color="#ff5722">{{item.imgyesNO?'图':''}}</Tag> - ({{item.men}})</p>
         <p>{{item.region}} - {{item.subrange}} - {{item.mian}}m²</p>
         <p v-if="item.price[0] !==0">{{item.price[0]}}元/m²*天(租)</p>
         <p v-if="item.price[1] !==0">{{item.price[1]}}元(售)</p>
         <p>{{item.ren}} - {{item.zuitime}}</p>
         <Row>
          <!-- <Col>{{item.yetype}}</Col> -->
            <Col>
              <Tag v-if="item.yetype !==null" type="border" :color="item.yetype[0] == 0 ? '#868686' : item.yetype[0] == 1?'blue':'green'">
                {{item.yetype[0] == 0 ? '未知' : item.yetype[0] == 1?'大':'小'}}
              </Tag>
              <Tag type="border" color="blue">{{item.method}}</Tag>
              <Tag type="border" color="blue">{{item.decoration}}</Tag>
              <Tag type="border" :color="item.followup=='无效'||item.followup=='已售'||item.followup=='已租'||item.followup=='我租' ? '#868686' : 'blue'">{{item.followup}}</Tag>
              <Tag type="border" color="blue">{{item.ren}}</Tag>
              <Tag type="border" :color="item.shelfyesNO ? '#ed3f14' : '#868686'">{{item.shelfyesNO?'上架':'下架'}}</Tag>
            </Col>
        </Row>
        <div class="ribot">
          <div><Button @click="piselu(0,item.id)" type="error">编辑</Button></div>
          <div><Button @click="piselu(1,item.id)" type="primary">跟进</Button></div>
        </div>
      </div>
      <Card class="cardlistno" style="min-height: 300px;text-align:center" v-if="HouseTableData.length ==0">
       <Icon type="sad-outline"></Icon>
        <p>没有数据</p>
      </Card>

        <div class="cf">
          <Page class="cf pages" :current="current" :total="totals" :page-size="pageSize"  @on-change="changepage" size="small"></Page>
        </div>
        <Spin size="large" fix v-if="loadings"></Spin>
   </Card>

    <!-- <Card class="padd10">
     <div class="cf">
     <div class="ovhidese">
      <Table class='tablese' :loading="loadings" width="100%" :columns="HouseTable" :data="HouseTableData" border highlight-row @on-sort-change="order"></Table>
        <div>
          <Page class="cf pages" :current="current" :total="totals" :page-size="pageSize"  @on-change="changepage" size="small"></Page>
        </div>
      </div>
      </div>
    </Card> -->

   </div>
</template>

<script>

import $ from 'jquery';
import axios from 'axios'
import Cookies from 'js-cookie';

export default {
    name: 'house',
      data () {
          return {
            ovhide:false,
            onst:-1,
            yeson:-1,
            yeson2:-1,
            yeson3:-1,
            yeson4:-1,
            childrenre:[],
            totals: 50, //总页数
            pageSize: 20, //每页显示
            current:1,
            spinShow: true,
            sesongs:'请搜索楼盘',
            modal2r: true,
            screense:false,// true 有搜索条件 false 无搜索条件
             options2: {
                    shortcuts: [
                        {
                            text: '一周',
                            value () {
                                const end = new Date();
                                const start = new Date();
                                start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
                                return [start, end];
                            }
                        },
                        {
                            text: '一个月',
                            value () {
                                const end = new Date();
                                const start = new Date();
                                start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
                                return [start, end];
                            }
                        },
                        {
                            text: '三个月',
                            value () {
                                const end = new Date();
                                const start = new Date();
                                start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
                                return [start, end];
                            }
                        }
                    ]
                },
            identitydata:[{
                    value: '小业主房源',
                    label: '小业主房源',
                    children: [
                        {
                            value: '二房东',
                            label: '二房东'
                        },
                        {
                            value: '转租客',
                            label: '转租客'
                        }
                    ]
                },{
                    value: '大业主房源',
                    label: '大业主房源',
                    children: [
                        {
                            value: '开发商',
                            label: '开发商'
                        },
                        {
                            value: '开发商代理',
                            label: '开发商代理'
                        },
                        {
                            value: '物业',
                            label: '物业'
                        },
                        {
                            value: '转租客',
                            label: '转租客'
                        },
                        {
                            value: '二房东',
                            label: '二房东'
                        },
                    ]
                }],//房源类型
            screens:{
               name:'',//房源名称
               regions:[],//所在区域
               ascription:'',//归属人
               FollowUp:'有效', //跟进类型
               metro:'', //最近地铁
               Renovation:'', //装修情况
               rent:{
                min:'',
                max:'',
               }, //租金区间
               minaji:{
                min:'',
                max:'',
               }, //面积区间
               zongshojia:{
                min:'',
                max:'',
               }, //总售价
               yesNO:'', //上架
               id:'',//ID
               yesNOimg:'',//图片
               identity:[],//业主类型
               times:[],//时间
               timese:[],
               key:'',
               order:'normal' //asc z desc f
             },
             loadingName: false,
             optionsName: [], //房源名称input
             loadingse:false,
              region: [], //商圈地区
              cityList: [],
              metros: [], //地铁
              gentype: [{
                        value: '新增',
                        label: '新增'
                    },
                    {
                        value: '有效',
                        label: '有效'
                    },
                    {
                        value: '待定',
                        label: '待定'
                    },
                    {
                        value: '已租',
                        label: '已租'
                    },
                    {
                        value: '已售',
                        label: '已售'
                    },
                    {
                        value: '无效',
                        label: '无效'
                    },
                     {
                        value: '我租',
                        label: '我租'
                    },
                    ], //跟进类型
              zhuangxtype:[{
                        value: '标准交付',
                        label: '标准交付'
                    },
                    {
                        value: '豪华装修',
                        label: '豪华装修'
                    },
                     {
                        value: '精装修',
                        label: '精装修'
                    },
                    {
                        value: '中等装修',
                        label: '中等装修'
                    },
                    {
                        value: '简装修',
                        label: '简装修'
                    },
                    {
                        value: '毛坯',
                        label: '毛坯'
                    },
                    ],//装修情况
              toogles:true,
              toogless:-1,//默认不展开
              loadings:true,
              HouseTable: [
                    {
                        title: 'ID',
                        align: 'center',
                        width: 70,
                        key: 'id'
                    },
                    {
                        title: '楼盘名称',
                        width: 200,
                        align: 'center',
                        key: 'name',
                        render: (h, params) => {
                           const row = params.row;
                           const text = row.imgyesNO ? '图' : '无';
                           const display = row.imgyesNO ? 'inline-block' : 'none';
                            return h('Poptip', {
                                props: {
                                    trigger: 'hover',
                                    content: row.region+'-'+row.subrange,
                                }
                            }, [
                                h('a', {
                                    props: {
                                        href: 'javascript:;'
                                    },
                                    style: {
                                        margin: '3px 0',
                                        display:"block",

                                    },
                                    on: {
                                        click: () => {
                                          let query = { deal_id: params.row.id};
                                            this.$router.push({
                                             name: 'house_look',
                                             query: query
                                            });
                                        }
                                    }
                                }, row.name),
                                h('span', {
                                    style: {
                                        margin: '2px 0',
                                        display: display,
                                        border:"1px solid #FF5722",
                                        color:"#FF5722",
                                        width: "20px",
                                    },
                                }, text)
                            ]);
                        }
                    },
                    {
                        title: '门牌号',
                        align: 'center',
                        width: 100,
                        sortable: 'custom',
                        key: 'men',
                        render: (h, params) => {
                            const row = params.row;
                            return h('Poptip', {
                                props: {
                                    trigger: 'hover',
                                    title: '门牌号',
                                    content: row.men,
                                },
                                style:{
                                  verticalAlign: '-10px'
                                }
                            }, [
                              h('div', {
                                style: {
                                  width:'60px',
                                  overflow: 'hidden',
                                  textOverflow: 'ellipsis',
                                  whiteSpace: 'nowrap',
                                  textAlign:'center'
                                }
                              }, row.men)
                            ]);
                        }
                    },
                    {
                        title: '面积',
                        align: 'center',
                        sortable: 'custom',
                        key: 'mian',
                        render: (h, params) =>{
                          // const dis = params.row.mian == null? '0' : params.row.mian;
                          return h('div', [
                                h('div', {}, params.row.mian+'m²'),
                            ]);
                        }
                    },
                    {
                        title: '租售价格',
                        align: 'center',
                        width: 150,
                        sortable: 'custom',
                        key: 'price',
                        render: (h, params) =>{
                          // const display = isNull(params.row.price[0]) ? 'none' : 'block'; 
                          // const displays = isNull(params.row.price[1]) || params.row.price[1] == 0? 'none' : 'block';
                          // console.log(params.row.price[0])
                          if (params.row.price[0] !==0) {
                              return h('div', [
                                 h('div', {
                                    style: {
                                        margin: '2px 0',
                                        display:'block'
                                    }
                                 }, params.row.price[0]+'元/m²*天(租)'),
                                 h('div', {
                                    style: {
                                        margin: '2px 0',
                                        display:'none'
                                    }
                                 }, params.row.price[1]+'元(售)'),
                            ]);
                          }
                          if (params.row.price[1] !==0) {
                              return h('div', [
                                 h('div', {
                                    style: {
                                        margin: '2px 0',
                                        display:'none'
                                    }
                                 }, params.row.price[0]+'元/m²*天(租)'),
                                 h('div', {
                                    style: {
                                        margin: '2px 0',
                                        display:'block'
                                    }
                                 }, params.row.price[1]+'元(售)'),
                            ]);
                          }

                          

                        }
                    },
                    {
                        title: '付款方式',
                        align: 'center',
                        key: 'method'
                    },
                    {
                        title: '装修',
                        align: 'center',
                        key: 'decoration'
                    },
                    {
                        title: '业主类型',
                        align: 'center',
                        key: 'yetype',
                        render: (h, params) => {
                            const row = params.row;
                            //0 未知 1 大 2 小
                            // console.log(row.yetype)
                            if (!row.yetype && typeof(row.yetype)!=undefined && row.yetype!=0){ 
                                return false
                              }　
                            const color = row.yetype[0] == 0 ? '#666' : row.yetype[0] == 1?'blue':'green';
                            const text = row.yetype[0] == 0 ? '未知' : row.yetype[0] == 1?'大':'小';
                            // const texts = row.yetype[0] == 0 ? '未知' : row.yetype[0] == 1?'大业主':'小业主';
                            return h('Poptip', {
                                props: {
                                    trigger: 'hover',
                                    title: row.yetype[1],
                                    content: row.yetype[2],
                                }
                            }, [
                              h('Tag', {
                                props: {
                                    type: 'dot',
                                    color: color
                                },
                                style: {
                                    zoom:0.8
                                }
                              }, text)
                            ]);
                        }
                    },
                    {
                        title: '跟进时间',
                        sortable: 'custom',
                        align: 'center',
                        key: 'zuitime',
                        render: (h, params) => {
                            const row = params.row;
                            return h('Poptip', {
                                props: {
                                    trigger: 'hover',
                                    title: "录入时间",
                                    content: row.entry,
                                }
                            }, row.zuitime)
                        }
                    },
                    {
                        title: '状态',
                        align: 'center',
                        width: 120,
                        key: 'zhuangt',
                        render: (h, params) => {
                          const row = params.row;
                          const text = row.shelfyesNO ? '上架' : '下架';
                          const type = row.shelfyesNO ? 'primary' : 'ghost';
                          const types = row.followup=='无效'||row.followup=='已售'||row.followup=='已租'||row.followup=='我租' ? 'ghost' : 'primary';
                            return h('div', [
                                h('Button', {
                                    props: {
                                        type: type,
                                        size: 'small'
                                    },
                                    style: {
                                        margin: '2px',
                                        zoom:0.5
                                    }
                                }, text),
                                h('Button', {
                                    props: {
                                        type: types,
                                        size: 'small'
                                    },
                                    style: {
                                        margin: '2px',
                                        zoom:0.5
                                    }
                                }, row.followup)
                            ]);
                        }
                    },
                    {
                        title: '归属人',
                        width: 100,
                        key: 'ren'
                    },
                    {
                        title: '操作',
                        align: 'center',
                        width: 150,
                        fixed: 'right',
                        key: 'mian',
                        render: (h, params) => {
                            return h('div', [
                                h('Button', {
                                    props: {
                                        type: 'error',
                                        size: 'small'
                                    },
                                    style: {
                                        margin: '2px'
                                    },
                                    on: {
                                        click: () => {
                                           let query = { deal_id: params.row.id};
                                            this.$router.push({
                                             name: 'houseadd_edit',
                                             query: query
                                            });
                                        }
                                    }
                                }, '编辑'),
                                h('Button', {
                                    props: {
                                        type: 'primary',
                                        size: 'small'
                                    },
                                    style: {
                                        margin: '2px'
                                    },
                                    on: {
                                        click: () => {
                                            let query = { deal_id: params.row.id};
                                            this.$router.push({
                                             name: 'house_follow',
                                             query: query
                                            });
                                        }
                                    }
                                }, '跟进')
                            ]);
                        }
                    },
                ],
                HouseTableData: []

          }
        },
        mounted(){
        var _this = this;
         this.ajaxName();//大楼名字
         axios({
              method:'post',
              url:'/api/region',
              headers:{Authorization:'Bearer '+Cookies.set('keya')},
           })
          .then(function (res) {
             // console.log(res.data.region)
             let data =[];
             for (var i = 0; i < res.data.region.length; i++) {
                 let a = {
                    value: res.data.region[i].value,
                    label: res.data.region[i].value,
                    children: res.data.region[i].children
                }
               data.push(a)
             }
             // console.log(data)
             _this.region = data
          })
          .catch(function (err) {
              _this.$Notice.error({title: '区域错误'});
          })

           axios({
              method:'post',
              url:'/api/metro',
              headers:{Authorization:'Bearer '+Cookies.set('keya')},
           })
          .then(function (res) {
            let data = res.data.metro;
            _this.metrosda = data;
            let metros = [];
              for (var i in data) {
                  let nea = {
                     value: i,
                     label: i
                    }
                metros.push(nea)
             }
             // console.log(metros)
             _this.metros = metros;
          })
          .catch(function (err) {
              _this.$Notice.error({title: '地铁错误'});
          })
           

          axios({
              method:'post',
              url:'/api/adminname',
              headers:{Authorization:'Bearer '+Cookies.set('keya')},
           })
          .then(function (res) {
            let data = res.data.message;
            _this.metrosda = data;
            let metros = [];
              for (var i in data) {
                  let nea = {
                     value: data[i],
                     label: data[i]
                    }
                metros.push(nea)
             }
             _this.cityList = metros;
          })
          .catch(function (err) {
              _this.$Notice.error({title: '人员错误'});
          })
         //默认数据 1
        

        // this.showHide(1);
        if (Cookies.getJSON('screense2') ==0 || Cookies.getJSON('screense2') == undefined ) {
             this.showHide(1); //类表
          }else{
             let se = Cookies.getJSON('screense2')
             let page = Cookies.getJSON('page2')

             this.sesongs = se.name
             this.screens.regions = se.regions
             this.screens.ascription = se.ascription
             this.screens.FollowUp = se.FollowUp
             this.screens.metro = se.metro
             this.screens.Renovation = se.Renovation
             this.screens.rent = se.rent
             this.screens.minaji = se.minaji
             this.screens.zongshojia = se.zongshojia
             this.screens.yesNO = se.yesNO
             this.screens.id = se.id
             this.screens.yesNOimg = se.yesNOimg
             this.screens.identity = se.identity
             this.screens.times = se.times
             this.screens.timese = se.timese
             this.screens.key = se.key
             this.screens.order = se.order

             if (page == undefined) {
               this.current = 1
               this.showHideseww(1)
             }else{
               this.current = page
               this.showHideseww(page); //类表
             }
             console.log(page)
             
          }

        },
        methods:{
          
          navsr(e){
            this.onst = e
          },
           changseee2(value){
            if (value == undefined) {
               this.screens.name = '',
               this.showHidese(1)
               this.onst = -1
            }else{
              this.showHidese(1)
              this.onst = -1
            }
          },
          clickyes(e,a){
            this.yeson= e
            this.yeson2= -1
            this.childrenre = this.region[e].children
            this.screens.regions[0] = a;
            this.screens.regions[1] = '';
            // console.log(a)
            // console.log(this.region[e].children)
          },
          clickyes2(e,a){
            this.yeson2= e
            this.screens.regions[1] = a;
          },
          conno(){
            this.onst = -1
            this.screens.regions = []
            this.showHidese(1)
          },
          conyes(){
            this.onst = -1
            this.showHidese(1)
          },
          clickyes4(){
            this.onst = -1
            this.yeson3= -1
            this.screens.FollowUp = ''
            this.showHidese(1)
          },
           clickyes3(e,a){
            this.onst = -1
            this.yeson3= e
            this.screens.FollowUp = a
            this.showHidese(1)
          },
          clickyes5(){
            this.onst = -1
            this.yeson4= -1
            this.screens.ascription = ''
            this.showHidese(1)
          },
           clickyes6(e,a){
            this.onst = -1
            this.yeson4= e
            this.screens.ascription = a
            this.showHidese(1)
          },
          piselu(e,a){
            if (e==0) {
              let query = { deal_id: a};
                this.$router.push({
                 name: 'houseadd_edit',
                 query: query
                });
            }else if(e==1){
              let query = { deal_id: a};
                this.$router.push({
                 name: 'house_follow',
                 query: query
                });
            }
          },
         ajaxName(e){
          let _this = this;
           _this.loading1 = true;
          axios({
              method:'post',
              url:'/api/louname?name=',
              headers:{Authorization:'Bearer '+Cookies.set('keya')},
           })
          .then(function (res) {
            _this.loading1 = false;
            let data = res.data.message;
            // console.log(data);
            _this.metrosda = data;
            let metros = [];
              for (var i in data) {
                  let nea = {
                     value: data[i],
                     label: data[i]
                    }
                metros.push(nea)
             }
             _this.optionsName = metros;
          })
          .catch(function (err) {
              _this.$Notice.error({title: '大楼名字错误'});
          })
         },
          remoteMethod(query){
           let _this = this;
             if(query !== ''){
              _this.loading1 = true;
              // console.log(query)
               axios({
                method:'post',
                url:'/api/louname?name='+query,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
                 })
                .then(function (res) {
                  _this.loading1 = false;
                  if(res.data.message.length !== 0){
                   let data = res.data.message;
                    // console.log(data);
                    _this.metrosda = data;
                    let metros = [];
                      for (var i in data) {
                          let nea = {
                             value: data[i],
                             label: data[i]
                            }
                        metros.push(nea)
                     }
                     _this.optionsName = metros;
                  }else{
                    _this.$Message.warning('没有找到'+query+', 请添加楼盘');
                  }
                  

                })
                .catch(function (err) {
                  _this.$Notice.error({title: '大楼名字错误'});
                })
             }else{
              _this.ajaxName();//大楼名字
             }
         },

            showHide(e){
              var _this = this;
              //房源默认没有条件
              _this.loadings = true;
               axios({
                method:'post',
                url:'/api/fangadmin2?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
             })
            .then(function (res) {
              _this.loadings = false;
              // console.log(res)
              
              _this.HouseTableData = res.data.message.data; //列表数据
              _this.pageSize = res.data.message.pageSize; //每页显示
              _this.totals = res.data.message.totals; //总数
              _this.$Message.success('房源数量：'+_this.totals+' 套');
            })
            .catch(function (err) {
                _this.$Notice.error({title: '房源类表错误'});
            })
            },

            showHidese(e){
              var _this = this;
              //房源有条件
              _this.loadings = true;
               axios({
                method:'post',
                url:'/api/fangadmin2?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
                 data:{
                  jo:_this.screens
                }
             })
            .then(function (res) {
              _this.loadings = false;
              // console.log(res.data.message)
              _this.HouseTableData = res.data.message.data; //列表数据
              _this.pageSize = res.data.message.pageSize; //每页显示
              _this.totals = res.data.message.totals; //总数
              _this.$Message.success('房源数量：'+_this.totals+' 套');
            })
             .catch(function (err) {
                _this.$Notice.error({title: '房源类表错误'});
             })
            },
            showHideseww(e){
              var _this = this;
              //房源有条件
              _this.loadings = true;
               axios({
                method:'post',
                url:'/api/fangadmin2?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
                 data:{
                  jo:Cookies.getJSON('screense2')
                }
             })
            .then(function (res) {
              _this.loadings = false;
              // console.log(res.data.message)
              _this.HouseTableData = res.data.message.data; //列表数据
              _this.pageSize = res.data.message.pageSize; //每页显示
              _this.totals = res.data.message.totals; //总数
              _this.$Message.success('房源数量：'+_this.totals+' 套');
            })
             .catch(function (err) {
                _this.$Notice.error({title: '房源类表错误'});
             })
            },
            order(e){
              //排序
              var _this = this;
              _this.screense = true; //有搜索条件
              let key = e.key;
              let order = e.order;
              _this.screens.key = key;
              _this.screens.order = order;
              _this.showHidese(1);
            },

            changepage(page) {
              var ele = document.getElementById('singlepagecon');
              ele.scrollTop = 0;
              //翻页
              var _this = this;
              _this.loadings = true;
              Cookies.set('page2', page); //权限
              if(_this.screense) {
                // console.log('%c有条件','color:red')
                _this.showHidese(page);
              }else{
                // console.log('%c无条件','color:blue')
                _this.showHide(page);
              }
            },
            addLOUPan(){
               this.$router.push({
                 name: 'houseadd'
                });
            },
            Edit(e){
              let query = { deal_id: e};
              this.$router.push({
                 name: 'buildingadd_edit',
                 query: query
                });
            },
            screenss(){
              this.onst = -1
              let _this = this;
               _this.screense = true; //有搜索条件
               _this.loadings = true;
               //搜索
               _this.showHidese(1);
               // console.log('%c搜索','color:red')
               Cookies.set('screense2', _this.screens); //权限
            },
            reson(){
              //重置
              this.onst = -1
              let _this = this;
              Cookies.set('screense2', 0); 
              _this.screense = false; //无搜索条件
              _this.showHide(1);
              _this.sesongs = '请搜索楼盘'
              _this.screens ={
               name:'',//房源名称
               regions:[],//所在区域
               ascription:'',//归属人
               FollowUp:'', //跟进类型
               metro:'', //最近地铁
               Renovation:'', //装修情况
               rent:{
                min:'',
                max:'',
               }, //租金区间
               minaji:{
                min:'',
                max:'',
               }, //面积区间
               zongshojia:{
                min:'',
                max:'',
               }, //总售价
               yesNO:'', //上架
               id:'',//ID
               yesNOimg:'',//图片
               identity:[],//业主类型
               times:[],//时间
               timese:[],
               key:'',
               order:'normal'
             }
            },

        },
        watch: {
          onst: {
              handler: function(val, oldVal) {
                 if (val !== -1) {
                   this.ovhide = true
                 }else{
                   this.ovhide = false
                 }
              },
              deep: true
          },
      }
};
</script>
