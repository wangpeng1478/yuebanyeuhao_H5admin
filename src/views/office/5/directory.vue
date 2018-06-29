
<style lang="less">
 .directory{
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
     .selectsNmae{
      .ivu-select-not-found{
           display:none
      }
   }
   .titims{
    background: #fff;
        padding: 5px;
    .lesr{
        float: left;
            margin: 4px 0 0 0;
      }
      .rigths{
        float:right;
        line-height: 33px;
        padding-right: 10px;
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
 }


 .directory{
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
</style>

<template>
   <div class="directory cf" :class="{hide:ovhide}">
   <pre>{{screens}}</pre>
      <div>
        <Form :model="screens" :label-width="80">
        <!-- se -->
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
                placeholder = "搜索楼盘"
                @on-change = "changseee2"
                :loading="loadingse">
                  <Option v-for="(option, index) in optionsName" :value="option.value" :key="index">{{option.label}}</Option>
              </Select>
            </Col>
          </Row>
           <Row class="sou2">
            <Col span="6"><p @click="navsr(0)" :class="{on:onst==0}" class="soup">所在区域<Icon type="arrow-down-b"></Icon></p></Col>
            <Col span="6"><p @click="navsr(1)" :class="{on:onst==1}" class="soup">最近地铁<Icon type="arrow-down-b"></Icon></p></Col>
            <Col span="6"><p @click="navsr(2)" :class="{on:onst==2}" class="soup">公司规模<Icon type="arrow-down-b"></Icon></p></Col>
            <Col span="6"><p @click="navsr(3)" :class="{on:onst==3}" class="soup">筛选<Icon type="funnel"></Icon></Icon></p></Col>
         </Row>
         <!-- 11111 -->
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
         <!-- 11111 -->
         <!-- 222222 -->
         <Row v-if="onst==1" class="cons">
          <Col class="ovhide">
            <p class="p2" :class="{on:yeson3== -1}" @click="clickyes4">全部</p>
            <p class="p2" :class="{on:yeson3==index}" v-for="(item,index) in metros" :key="item.value" @click="clickyes3(index,item.value)">{{item.value}}</p>
          </Col>
        </Row>
         <!-- 222222 -->
         <!-- 33333   -->
         <Row v-if="onst==2" class="cons">
      <Col class="ovhide">
        <p class="p2" @click="strenc('0')" :class="{on:screens.scalex == ''}" >全部</p>
        <p class="p2" @click="strenc('20人以下')" :class="{on:screens.scalex == '20人以下'}" >20人以下</p>
        <p class="p2" @click="strenc('20-50人')" :class="{on:screens.scalex == '20-50人'}" >20-50人</p>
        <p class="p2" @click="strenc('50-100人')" :class="{on:screens.scalex == '50-100人'}" >50-100人</p>
        <p class="p2" @click="strenc('100-200人')" :class="{on:screens.scalex == '100-200人'}" >100-200人</p>
        <p class="p2" @click="strenc('200-500人')" :class="{on:screens.scalex == '200-500人'}" >200-500人</p>
        <p class="p2" @click="strenc('500-800人')" :class="{on:screens.scalex == '500-800人'}" >500-800人</p>
        <p class="p2" @click="strenc('800-1500人')" :class="{on:screens.scalex == '800-1500人'}" >800-1500人</p>
        <p class="p2" @click="strenc('1500人以上')" :class="{on:screens.scalex == '1500人以上'}" >1500人以上</p>
      </Col>
    </Row>
         <!-- 33333   -->
         <!-- 44444 -->
          <Row v-if="onst==3" class="cons" style="padding: 5px 10px 0 10px;border-top: 1px solid #eee;">
           <Col class="ovhide"> 
               <FormItem label="所在楼层">
                    <Input v-model="screens.layers">
                        <span slot="append">层</span>
                    </Input>
               </FormItem>
                <FormItem label="公司名称">
                    <Input v-model="screens.companyname">
                       
                    </Input>
               </FormItem>
               <FormItem label="公司行业">
                 <select v-model="screens.tradex" class="selectUI">
                          <option value="IT|通信|电子|互联网">IT|通信|电子|互联网</option>
                          <option value="金融业">金融业</option>
                          <option value="房地产|建筑">房地产|建筑</option>
                          <option value="贸易|批发|零售|租赁业">贸易|批发|零售|租赁业</option>
                          <option value="生产|加工|制造">生产|加工|制造</option>
                          <option value="交通|运输|物流|仓储">交通|运输|物流|仓储</option>
                          <option value="服务业">服务业</option>
                          <option value="文化|传媒|娱乐|体育">文化|传媒|娱乐|体育</option>
                          <option value="文体教育|工艺美术">文体教育|工艺美术</option>
                          <option value="能源|矿产|环保">能源|矿产|环保</option>
                          <option value="商业服务">商业服务</option>
                          <option value="政府|非盈利机构">政府|非盈利机构</option>
                          <option value="农|林|牧|渔">农|林|牧|渔</option>
                          <option value="机械设备|医疗器械">机械设备|医疗器械</option>
                          <option value="其他">其他</option>
                  </select>
               </FormItem>
               <FormItem label="是否在租">
                   <RadioGroup v-model="screens.grade" type="button">
                        <Radio label="是">是</Radio>
                        <Radio label="否">否</Radio>
                    </RadioGroup>
              </FormItem>
           </Col>
           <ButtonGroup class="botonbur">
              <Button type="ghost" icon="reply" @click='reson'>重置</Button>
              <Button type="primary" icon="ios-search" @click='screenss'>确认</Button>
            </ButtonGroup>
           </Row>
         <!-- 44444 -->
        </div>
        <!-- se -->
         
         
        </Form>
      </div>
        <div class='titims' style="margin:5px 0">
         <div class="cf">
          <Button class="lesr" type="primary" @click="addLOUPan" shape="circle" size="small" icon="ios-plus-outline">添加名录</Button>
            <div class="rigths">楼盘：<b>{{totals}}</b>套</div>
            <div class="rigths">企业名录：<b>{{totals1}}</b>条</div>
         </div>
        </div>
         <div v-if='datale.length !== 0' style="background: #fff;padding: 5px;">
            <div class="cf">
               <div class="lstable cf">
                  <div class="tableUl">
                       <div class="ls" v-for="(item, index) in datale" :key="index">
                        <div class="li cf">
                          <div class="le" @click.prevent="showHide(index,item.ofid)">
                            <b>{{item.name}}</b>
                          </div>
                          <div class="rig">
                            <a href="#" @click.prevent="showHide(index,item.ofid)">查看详情 </a>
                             <!--  <Tooltip content="打印" placement="top" v-if="access.ente03">
                                  <a href="#" @click.prevent="printer(item.ofid,item.name)"><Icon style="vertical-align: middle" size='20' color="#5c6b77" type="printer"></Icon></a>
                              </Tooltip> -->
                          </div>
                        </div>
                          <Table v-if="toogless == index" :loading="loadings" width="100%" :columns="HouseTable" :data="HouseTableData" highlight-row></Table>
                      </div>

                  </div>
                </div>
                 <Page class="cf pages" :total="totals" :page-size="pageSize"  @on-change="changepage" size="small"></Page>
            </div>
            <Spin size="large" fix v-if="spinShow"></Spin>
        </div>
        <Card class="cardlistno" style="min-height: 500px;text-align:center" v-else>
           <Icon type="sad-outline"></Icon>
        <p>没有数据</p>
           <Spin size="large" fix v-if="spinShow"></Spin>
        </Card>

   </div>
</template>

<script>
import axios from 'axios'
import Cookies from 'js-cookie';

export default {
    name: 'directory',
      data () {
          return {
            ovhide:false,
            onst:-1,
            yeson:-1,
            yeson2:-1,
            yeson3:-1,
            yeson4:-1,
            childrenre:[],
            totals: 0, //总页数
            pageSize: 0, //每页显示
            totals1:0,
            spinShow: true,
            screense:false,// true 有搜索条件 false 无搜索条件
            optionsName: [], //房源名称input
            region:[],
            metros: [], //地铁
            access:{},//权限
            loadingse:false,
            loadings:true,
            toogless:-1,//默认不展开
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
            screens:{
               name:'',//楼盘
               regions:[],//所在区域
               metro:'',//最近地铁
               layers:'',//所在楼层
               companyname:'',//公司名称
               scalex:'',//公司规模
               tradex:'',//公司规模
               timese:[],//租约到期
               grade:'',//是否在租
            },
            datale:[], //表
            HouseTable:[
              {
                type: 'index',
                width: 60,
                align: 'center'
              },
              
              {
                title: '公司名称',
                key: 'gname',
                width: 230,
                align: 'center',
                render: (h, params) => {
                    const row = params.row;
                    const baidu = 'https://www.baidu.com/s?&wd='+row.gname;
                    const qichacha = 'http://www.qichacha.com/search?key='+row.gname;
                    const tianyancha = 'https://www.tianyancha.com/search?key='+row.gname;
                    return h('Poptip', {
                        props: {
                            trigger: 'hover',
                            title: '点击查询企业',
                        }
                    }, [
                      h('div',{style:{cursor:'pointer'}}, row.gname),
                      h('a', {
                          slot: 'content',
                          attrs: {
                              target: '_blank',
                              href:baidu
                          },
                          style: {
                              margin: '5px',
                              display:'block',
                              borderBottom:'1px solid #eee',
                              paddingBottom:'5px'
                          }
                        }, row.gname+'(百度搜索)'),
                      h('a', {
                          slot: 'content',
                          attrs: {
                              target: '_blank',
                              href:qichacha
                          },
                          style: {
                              margin: '5px',
                              display:'block',
                              borderBottom:'1px solid #eee',
                              paddingBottom:'5px'
                          }
                        }, row.gname+'(企查查搜索)'),
                      h('a', {
                          slot: 'content',
                          attrs: {
                              target: '_blank',
                              href:tianyancha
                          },
                          style: {
                              margin: '5px',
                              display:'block',
                              borderBottom:'1px solid #eee',
                              paddingBottom:'5px'
                          }
                        }, row.gname+'(天眼查搜索)'),
                    ]);
                }
              },
              {
                title: '单元号',
                align: 'center',
                sortable: true,
                width: 150,
                render: (h, params) => {
                 const row = params.row;
                  return h('div', [
                      h('span', {
                      }, row.floorx+"F - "),
                       h('span', {
                      }, row.hnumber )
                  ]);
               }
              },
              {
              title: '操作',
              key: 'action',
              width: 130,
              align: 'center',
              fixed: 'right',
              render: (h, params) => {
                  return h('div', [
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
                                   let query = { deal_id: params.row.qyid};
                                    this.$router.push({
                                     name: 'directory_look',
                                     query: query
                                    });
                              }
                          }
                      }, '查看'),
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
                                   let query = { deal_id: params.row.qyid};
                                    this.$router.push({
                                     name: 'directoryadd_st',
                                     query: query
                                    });
                              }
                          }
                      }, '编辑')
                  ]);
              }
             }
            ],
            HouseTableData:[] 
          }
        },
        mounted(){
          this.accesse();
          this.ajaxName();
          this.quyu();
          this.datie();
          this.buildingls(1);
        },
        methods:{
          navsr(e){
            this.onst = e
          },
           changseee2(value){
            if (value == undefined) {
               this.buildingls(1)
               this.onst = -1
            }else{
              this.buildinglse(1)
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
            this.onst = -1
            this.buildinglse(1)
          },
          conno(){
            this.onst = -1
            this.screens.regions = ['','']
            this.buildinglse(1)
          },
          conyes(){
            this.onst = -1
            this.buildinglse(1)
          },
          clickyes4(){
            this.onst = -1
            this.yeson3= -1
            this.screens.metro = ''
            this.buildinglse(1)
          },
           clickyes3(e,a){
            this.onst = -1
            this.yeson3= e
            this.screens.metro = a
            this.buildinglse(1)
          },
          strenc(e){
            this.onst = -1
            if (e==0) {
              this.buildingls(1)
            }else{
              this.screens.scalex = e;
              this.buildinglse(1)
            }
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
          accesse(){
             let _this = this;
             axios({
                method: 'post',
                url: '/api/power',
                headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
              })
              .then(function(res) {
                   Cookies.set('auth', res.data.power); //权限
                  _this.access = res.data.power;
              })
              .catch(function(err) {
                  _this.$Notice.error({ title: '权限获取错误' });
              })
          },
         datie(){
            let _this = this;
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
         },
         quyu(){
           let _this = this;
            axios({
              method:'post',
              url:'/api/region',
              headers:{Authorization:'Bearer '+Cookies.set('keya')},
           })
            .then(function (res) {
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
         addLOUPan(){
            this.$router.push({
             name: 'directory_add'
            });
         },
         buildingls(e){
            let _this = this;
             _this.spinShow = true;
            axios({
                method:'post',
                url:'/api/entelist?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
             })
            .then(function (res) {
              _this.spinShow = false;
              _this.datale = res.data.message.data;
              _this.pageSize = res.data.message.pageSize;
              _this.totals = res.data.message.totals;
              _this.totals1 = res.data.message.totals2
              _this.$Message.success('楼盘：'+_this.totals+' 套');
              _this.$Message.success('企业名录：'+_this.totals1+' 条');
            })
            .catch(function (err) {
                _this.$Notice.error({title: '类表错误'});
            })
          },
          buildinglse(e){
            let _this = this;
             _this.spinShow = true;
            axios({
                method:'post',
                url:'/api/entelist?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
                data:{
                  jo:_this.screens
                }
             })
            .then(function (res) {
              _this.spinShow = false;
              _this.datale = res.data.message.data;
              _this.pageSize = res.data.message.pageSize;
              _this.totals = res.data.message.totals;
               _this.totals1 = res.data.message.totals2
              _this.$Message.success('楼盘：'+_this.totals+' 套');
              _this.$Message.success('企业名录：'+_this.totals1+' 条');
            })
            .catch(function (err) {
                _this.$Notice.error({title: '类表错误'});
            })
          },
         showHide(e,b){
            //展开 收缩
              var _this = this;
               _this.toogless = e;
               //名录
              _this.loadings = true;
                  axios({
                      method:'post',
                      url:'/api/entelistact?ofid='+b,
                      headers:{Authorization:'Bearer '+Cookies.set('keya')},
                       data:{
                         jo:_this.screens
                       }
                   })
                  .then(function (res) {
                   _this.loadings = false;
                   _this.HouseTableData = res.data.message
                  })
                  .catch(function (err) {
                      _this.$Notice.error({title: '名录错误'});
                  })

            },
           changepage(page) {
              //翻页
              var _this = this;
              _this.spinShow = true;
              _this.toogless = -1;//防止分页加载index
              if(_this.screense) {
                _this.buildinglse(page)
              }else{
                _this.buildingls(page); //无
              }
            },
            screenss(){
              this.onst = -1
              let _this = this;
               _this.screense = true; //有搜索条件
               _this.loadings = true;
                _this.toogless = -1;//防止分页加载index
               //搜索
               _this.buildinglse(1);
            },
            reson(){
              this.onst = -1
              //重置
              let _this = this;
              _this.screense = false; //无搜索条件
               _this.toogless = -1;//防止分页加载index
              _this.buildingls(1);
              _this.screens ={
                   name:'',//楼盘
                   regions:[],//所在区域
                   metro:'',//最近地铁
                   layers:'',//所在楼层
                   companyname:'',//公司名称
                   scalex:'',//公司规模
                   tradex:'',//公司规模
                   timese:[],//租约到期
                   grade:'',//是否在租
             }
            },
            printer(e,a){
             let query = { 
              deal_id: e,
              name:a
            };
                this.$router.push({
                 name: 'print_s',
                 query: query
                });
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

