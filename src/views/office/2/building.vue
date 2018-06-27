<style lang="less">
 .building{
  padding-top: 77px;

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
      padding:7px;
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
</style>

<template>
   <div class="building cf" :class="{hide:ovhide}">
   <!-- ovhide -->
    <pre>{{screens}}</pre>
    <pre>{{region}}</pre>
    <Form :model="screens" :label-width="80">
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
           <FormItem label="ID">
                 <Input v-model="screens.id"></Input>
            </FormItem>
             <FormItem label="是否上架">
                  <RadioGroup v-model="screens.yesNO" type="button">
                      <Radio label="上架"></Radio>
                      <Radio label="下架"></Radio>
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
      <Button class="lesr" type="primary" @click.prevent="addLOUPan" shape="circle" icon="ios-plus-outline">添加楼盘</Button>
       <div class="rigths">楼盘数量：<b>{{totals}} </b>套</div>
     </div>
    </Card>
    <div style="position:relative">
   
    <Card class="padd10" v-if='officeDta.length !== 0'>
    <div class="cf">
      <div class="lstable cf">
        <div class="tableUl">
         <div class="ls" v-for="(item, index) in officeDta" :key="index">
          <div class="li cf">
            <div class="le" @click="buildinglooks(item.uniqidof)">
              <b>楼盘名称：{{item.name}}</b> ID: {{item.id}}({{item.esa== null? 0:item.esa}}) {{item.diyu}} {{item.ditie}} {{item.station}}
            </div>
            <div class="rig">
              <a href="#" @click.prevent="showHide(index,item.id,item.esa)">查看房源</a>
              <a href="#" @click.prevent="Edit(item.uniqidof)">编辑</a>
            </div>
          </div>
        <div style="overflow:auto;">
          <Table style="min-width: 1190px;" v-if="toogless == index" :loading="loadings" width="100%" :columns="HouseTable" :data="HouseTableData" highlight-row></Table>
        </div>
        </div>
        </div>
      </div>
      <Page class="cf pages" :current="current" :total="totals" :page-size="pageSize" @on-change="changepage" size="small"></Page>
      </div>
    </Card>
    <Card class="cardlistno" style="min-height: 300px;text-align:center" v-else>
       <Icon type="sad-outline"></Icon>
        <p>没有数据</p>
    </Card>
    <Spin size="large" fix v-if="spinShow"></Spin>
    </div>
   </div>
</template>

<script>

import $ from 'jquery';
import axios from 'axios'
import Cookies from 'js-cookie';

export default {
    name: 'building',
      data () {
          return {
            totals: 50, //总页数
            pageSize: 20, //每页显示
            current:1,
            ovhide:false,
            onst:-1,
            yeson:-1,
            yeson2:-1,
            yeson3:-1,
            yeson4:-1,
            childrenre:[],
            spinShow: true,
            sesongs:'请搜索楼盘',
            screense:false,// true 有搜索条件 false 无搜索条件
            screens:{
               name:'',//楼盘名称
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
               yesNO:'',
               id:''
             },
             loadingName: false,
             optionsName: [], //楼盘名称input
             loadingse: false,
             region: [{
                    value: '黄浦',
                    label: '黄浦',
                    children: [{
                        value: '八佰伴',
                        label: '八佰伴',
                    }]
                },{
                    value: '普陀',
                    label: '普陀',
                    children: [{
                        value: '中山公园',
                        label: '中山公园',
                    }]
                }], //商圈地区
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
              officeDta:[],
              HouseTable: [
                    {
                        title: 'ID',
                        align: 'center',
                        width: 100,
                        key: 'id'
                    },
                    {
                        title: '门牌号',
                        align: 'center',
                        key: 'men'
                    },
                    {
                        title: '面积',
                        align: 'center',
                        sortable: true,
                        key: 'mian',
                        render: (h, params) =>{
                          return h('div', [
                                h('div', {}, params.row.mian+'m²'),
                            ]);
                        }
                    },
                    {
                        title: '价格',
                        align: 'center',
                        key: 'jia',
                        render: (h, params) => {
                            return h('div', [
                                h('div', {}, '预估价格 '+params.row.money3+' 元/m²'),
                                h('div', {}, '业主报价 '+params.row.money1+' 元/m²')
                            ]);
                        }
                    },
                    {
                        title: '业主类型',
                        align: 'center',
                        key: 'yetype',
                        render: (h, params) => {
                            const row = params.row;
                            //0 未知 1 大 2 小
                            const color = row.yetype[0] == 0 ? '#666' : row.yetype[0] == 1?'blue':'green';
                            const text = row.yetype[0] == 0 ? '未知' : row.yetype[0] == 1?'大业主':'小业主';
                            return h('Poptip', {
                                props: {
                                    trigger: 'hover',
                                    title: text,
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
                        },
                        filters: [
                            {
                                label: '未知',
                                value: 0
                            },
                            {
                                label: '大业主',
                                value: 1
                            },
                            {
                                label: '小业主',
                                value: 2
                            }
                        ],
                        filterMultiple: false,
                        filterMethod (value, row) {
                            if (value === 0) {
                                return row.yetype[0] ===0;
                            } else if (value === 1) {
                                return row.yetype[0] ===1;
                            }else if (value === 2) {
                                return row.yetype[0] ===2;
                            }
                        }
                    },
                    {
                        title: '最新跟进',
                        sortable: true,
                        align: 'center',
                        key: 'zuitime'
                    },
                    {
                        title: '状态',
                        align: 'center',
                        key: 'zhuangt'
                    },
                    {
                        title: '归属人',
                        align: 'center',
                        key: 'ren'
                    },
                    {
                        title: '操作',
                        align: 'center',
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
                HouseTableData: [], //房源

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
          
          
          
          if (Cookies.getJSON('screense') ==0 || Cookies.getJSON('screense') == undefined ) {
             this.buildingls(1); //类表
          }else{
             let se = Cookies.getJSON('screense')
             let page = Cookies.getJSON('page1')
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

             if (page == undefined) {
               this.current = 1
               this.buildinglsew(1)
             }else{
               this.current = page
               this.buildinglsew(page); //类表
             }
             console.log(page)
             
          }
        },
        methods:{
          navsr(e){
            this.onst = e
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
          clickyes3(e,a){
            this.onst = -1
            this.yeson3= e
            this.screens.FollowUp = a
            this.buildinglse(1)
          },
          clickyes4(){
            this.onst = -1
            this.yeson3= -1
            this.screens.FollowUp = ''
            this.buildinglse(1)
          },
          clickyes5(){
            this.onst = -1
            this.yeson4= -1
            this.screens.ascription = ''
            this.buildinglse(1)
          },
           clickyes6(e,a){
            this.onst = -1
            this.yeson4= e
            this.screens.ascription = a
            this.buildinglse(1)
          },
          conyes(){
            this.onst = -1
            this.buildinglse(1)
          },
          conno(){
            this.onst = -1
            this.screens.regions = []
            this.buildinglse(1)
          },
          changseee2(value){
            if (value == undefined) {
               this.screens.name = '',
               this.buildinglse(1)
               this.onst = -1
            }else{
              this.buildinglse(1)
              this.onst = -1
            }
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
          buildingls(e){
            let _this = this;
             _this.spinShow = true;
            axios({
                method:'post',
                url:'/api/louadmin?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
             })
            .then(function (res) {
              _this.spinShow = false;
              // console.log(res)
              _this.officeDta = res.data.message.data;
              _this.pageSize = res.data.message.pageSize;
              _this.totals = res.data.message.totals;
              _this.$Message.success('楼盘数量：'+_this.totals+' 套');
            })
            .catch(function (err) {
                _this.$Notice.error({title: '类表错误'});
            })
          },
          buildinglse(e){
            let _this = this;
            // console.log(_this.screens)
             _this.spinShow = true;
            axios({
                method:'post',
                url:'/api/louadmin?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
                data:{
                  jo:_this.screens
                }
             })
            .then(function (res) {
              _this.spinShow = false;
              _this.officeDta = res.data.message.data;
              _this.pageSize = res.data.message.pageSize;
              _this.totals = res.data.message.totals;
              _this.$Message.success('楼盘数量：'+_this.totals+' 套');
            })
            .catch(function (err) {
                _this.$Notice.error({title: '类表错误'});
            })
          },
          buildinglsew(e){
            let _this = this;
            // console.log(_this.screens)
             _this.spinShow = true;
            axios({
                method:'post',
                url:'/api/louadmin?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
                data:{
                  jo:Cookies.getJSON('screense')
                }
             })
            .then(function (res) {
              _this.spinShow = false;
              _this.officeDta = res.data.message.data;
              _this.pageSize = res.data.message.pageSize;
              _this.totals = res.data.message.totals;
              _this.$Message.success('楼盘数量：'+_this.totals+' 套');
            })
            .catch(function (err) {
                _this.$Notice.error({title: '类表错误'});
            })
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
            showHide(e,b,r){
               //查看
              var _this = this;
              if (r == null || r ==0) {
                _this.$Message.warning('没有房源');
              }else{
               _this.toogless = e;
              //房源
              _this.loadings = true;
              axios({
                  method:'post',
                  url:'/api/fangadmin1?id='+b,
                  headers:{Authorization:'Bearer '+Cookies.set('keya')},
               })
              .then(function (res) {
               _this.loadings = false;
               _this.HouseTableData = res.data.message.data
                // console.log( JSON.stringify(res.data.message.data["0"].yetype))
              })
              .catch(function (err) {
                  _this.$Notice.error({title: '楼盘错误'});
              })
              }
            },
            changepage(page) {
              var ele = document.getElementById('singlepagecon');
              ele.scrollTop = 0;
              
              //翻页
              var _this = this;
              _this.spinShow = true;
              _this.toogless = -1;//防止分页加载index
              Cookies.set('page1', page); //权限

              if(_this.screense) {
                console.log('%c有条件','color:red')
                _this.buildinglse(page)
              }else{
                console.log('%c无条件','color:blue')
                _this.buildingls(page); //类表
              }
            },
            addLOUPan(){
               this.$router.push({
                 name: 'buildingsadd'
                });
            },
            Edit(e){
              let query = { deal_id: e};
              this.$router.push({
                 name: 'buildingadd_edit',
                 query: query
                });
            },
            buildinglooks(e){
              let query = { deal_id: e};
              this.$router.push({
                 name: 'building_look',
                 query: query
                });
            },
            screenss(){
              let _this = this;
              this.onst = -1
              // console.log(this.screens)
              _this.toogless = -1;//防止分页加载index
              _this.screense = true; //有搜索条件
              Cookies.set('screense', _this.screens); //权限
              _this.spinShow = true; //table looing
              
              //搜索
              axios({
               method: 'post',
               url: '/api/louadmin',
               headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
               data:{
                 jo:_this.screens
               }
               })
               .then(function(res) {
                _this.spinShow = false;
                 // console.log(res)
                 _this.officeDta = res.data.message.data;
                 _this.pageSize = res.data.message.pageSize;
                 _this.totals = res.data.message.totals;
                 _this.$Message.success('楼盘数量：'+_this.totals+' 套');

               })
               .catch(function(err) {
                   _this.$Notice.error({ title: '搜索错误' });
               })

            },
            reson(){
              //重置
              this.onst = -1
              let _this = this;
              _this.buildingls(1); //类表
              _this.screense = false; //无搜索条件
               Cookies.set('screense', 0); 
              _this.sesongs = '请搜索楼盘'
              _this.toogless = -1;//防止分页加载index
              // _this.spinShow = true; //table looing
              this.screens = {
               name:'',//楼盘名称
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
               yesNO:'',
               id:''
             }

            }

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
