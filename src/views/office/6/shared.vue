
<style lang="less">
 .shared{
  padding-top: 77px;
     .selectsNmae{
      .ivu-select-not-found{
        display:none
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
   code {
    display: inline-block;
    background: #ededed;
    font-family: Consolas,Monaco,Andale Mono,Ubuntu Mono,monospace;
    margin: 0 3px;
    padding: 1px 5px;
    border-radius: 3px;
    color: #666;
    border: 1px solid #c5c3c3;
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
  .titims{
    background:#fff;
    margin: 5px 0;
    padding: 5px;
  }
}
  
 .shared{
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
.shared{
  .classtable{
    border-bottom:1px solid #eee;
    padding:6px;
    margin:0 0 8px 0;
    background: #fff;
   .hd{
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
   }
    .ivu-tag {
    padding: 0 2px;
    font-size: 11px;
    height: 20px;
    line-height: 20px;
    margin: 0;
    zoom: 0.8;
    vertical-align: text-top;
    background: #fff !important;
  }
   .tcbtiele{
     background:#e6f5ff;
     border:1px solid #c1e7ff;
     padding: 2px;
     .ivu-col-span-20{
       font-size: 15px;
       font-weight: 600;
       padding-left: 5px;
     }
     .ivu-col-span-4{
      line-height: 23px;
     }
   }
   .tcbbody{
     padding:5px;
     border:1px solid #c1e7ff;
     border-top:none;
     .tcbbodyh3{
       font-size: 13px;
       font-weight: 300;
     }
     .ivu-col{
       margin-bottom: 3px;
     }
     .hr{
       border-bottom: 1px dashed #eee;
       margin: 5px 0;
     }
   }
  }
  .api table {
    font-family: Consolas,Menlo,Courier,monospace;
    font-size: 12px;
    border-collapse: collapse;
    border-spacing: 0;
    empty-cells: show;
    border: 1px solid #e9e9e9;
    width: 100%;
    margin-bottom: 24px
}

.api table th {
    background: #f7f7f7;
    white-space: nowrap;
    color: #5c6b77;
    font-weight: 600
}

.api table td,.api table th {
    border: 1px solid #e9e9e9;
    padding: 8px 16px;
    text-align: left
}

.api table td ul li {
    font-size: 12px!important
}
}

</style>

<template>
   <div class="shared cf" :class="{hide:ovhide}">
    <pre>{{datas}}</pre>
        <Form :model="screens" :label-width="80">

       <div class="navfix">
          <Row class="sou1">
            <Col>
                <Select v-model="screens.brands" filterable clearable @on-change="changseee2">
                    <Option v-for="item in metross" :value="item.value" :key="item.value">{{ item.label }}</Option>
                </Select>
            </Col>
          </Row>

          <Row class="sou2">
            <Col span="6"><p @click="navsr(0)" :class="{on:onst==0}" class="soup">所在区域<Icon type="arrow-down-b"></Icon></p></Col>
            <Col span="6"><p @click="navsr(1)" :class="{on:onst==1}" class="soup">最近地铁<Icon type="arrow-down-b"></Icon></p></Col>
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
          <p class="p2" :class="{on:yeson3==index}" v-for="(item,index) in metros" :key="item.value" @click="clickyes3(index,item.value)">{{item.value}}</p>
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
              <FormItem label="房源名称">
                    <Select v-model="screens.name" 
                    class="selectsNmae" 
                  filterable
                  clearable
                  remote
                  :remote-method="remoteMethod"
                  placeholder = '请搜索楼盘'>
                      <Option v-for="(option, index) in optionsName" :value="option.value" :key="index">{{option.label}}</Option>
                  </Select>
              </FormItem>
                <FormItem label="价格区间">
                 <div class="input-group">
                  <input v-model="screens.rentmin" type="text" maxlength="8">
                  <input v-model="screens.rentmax" type="text" maxlength="8">
                  <span>元</span>
                </div>
              </FormItem>
                <FormItem label="网点ID">
                  <Input v-model="screens.id"></Input>
              </FormItem>
               <FormItem label="是否上架">
                   <RadioGroup v-model="screens.grade" type="button">
                        <Radio label="1">是</Radio>
                        <Radio label="2">否</Radio>
                    </RadioGroup>
              </FormItem>
            </Col>
        </Col>
        <ButtonGroup class="botonbur">
          <Button type="ghost" icon="reply" @click='reson'>重置</Button>
          <Button type="primary" icon="ios-search" @click='screenss'>确认</Button>
        </ButtonGroup>
      </Row>


        </div>


        <!--   
         <Row>
           <Col :xs="24" :sm="24" :md="24" :lg="24" style="text-align:center">
             <Button size="small" @click='screenss' type="primary" icon="ios-search">查询</Button>
             <Button size="small" @click='reson' type="ghost" icon="reply">重置</Button>
           </Col>
        </Row> -->
        </Form>

        <div class='titims'>
         <div class="cf">
            <Button style="display:inline-block" type="primary" @click="addLOUPan" size="small" shape="circle" icon="ios-plus-outline">添加品牌</Button>
            <div style="display:inline-block">品牌：<b>{{totals}}</b>个</div>
            <div style="display:inline-block">网点：<b>{{totals2}}</b>个</div>
            <div style="display:inline-block">工位：<b>{{totals3}}</b>个</div>
         </div>
        </div>

        <!-- tablese -->
        <!-- tablese -->
        <div class="cf" style="margin:0 0 5px 0">
           <div v-for="(n, index) in datas" :key="index" class="classtable">
               <Row class="tcbtiele">
                  <Col span="20" class="hd">
                    <span>{{n.name}} - ({{n.outlets.length}})</span>
                    <Tag type="border" color="#ff5722" v-if="n.imgyes">图</Tag>
                  </Col>
                  <Col span="4" class="hd">
                    <a href="javascript:;" @click.prevent="sharedaddst(n.id)">查看详情</a>
                  </Col>
              </Row>
              <Row v-for="(s, index) in n.outlets" :key="s.length" class="tcbbody">
                <Col class="hd">
                  <span class="tcbbodyh3">{{s.oname}}</span> <Tag type="border" color="#ff5722" v-if="s.imgyeso">图</Tag> <span>{{s.type}}</span>
                </Col>
                <Col>{{s.address}}</Col>
                <Col>{{s.attribution}} - {{s.time}}</Col>
                <div class="hr"></div>
                <Row>
                <Col span="12">
                   <Poptip v-if="s.gnumeral !==0" placement="bottom-start" trigger="click" @on-popper-show="Poptipsr(s.oid,s.gnumeral)">
                      <Button size="small" type="primary">{{s.gnumeral}}</Button>
                      <div class="api" slot="content">
                          <table>
                              <thead>
                                  <tr>
                                      <th>办公室类型</th>
                                      <th>单价</th>
                                      <th>状态</th>
                                  </tr>
                              </thead>
                              <tbody>
                                  <tr v-for="(ss, index) in spinShowPoptipsrdata" :key="index">
                                      <th>{{ss.type}}</th>
                                      <th><code>{{ss.nus}} </code>元/工位/月</th>
                                      <th>
                                      <code :style="{background : ss.yes=='上架'?'#2d8cf0':'#f7f7f7',color:ss.yes=='上架'?'#fff':'#666'}">{{ss.yes}}</code>
                                      </th>
                                  </tr>
                                  <tr v-if="spinShowPoptipsrdata.length == 0">
                                    <th colspan="3">没有工位</th>
                                  </tr>
                              </tbody>
                          </table>
                          <Spin v-if="spinShowPoptipsr" fix>加载中...</Spin>
                      </div>
                  </Poptip>
                </Col>


                <Col span="12" style="text-align:right">
                  <Button size="small" type="ghost" @click="changegong(s.oid)">工位</Button>
                  <Button size="small" type="error" @click="lookgong(s.oid,s.ofid,s.uniqidof)">跟进</Button>
                </Col>

              </Row>
                
              </Row>



           </div>
           <div v-if="datas.length ==0">
              <Card class="cardlistno" style="min-height: 300px;text-align:center">
                 <Icon type="sad-outline"></Icon>
                  <p>没有数据</p>
              </Card>
           </div>

        </div>
            <div style="padding:20px 0 200px 0;background: #fff;">
                <Page class="cf" style="float: right;" :total="totals" :page-size="pageSize" size="small" @on-change="changepage"></Page>
              </div>
            <Spin size="large" fix v-if="spinShow"></Spin>
        <!-- tablese -->
        <!-- tablese -->

   </div>
</template>

<!-- 价格 -->
<!-- 网点ID -->
<script>
import axios from 'axios'
import Cookies from 'js-cookie';

export default {
    name: 'shared',
      data () {
          return {
            ovhide:false,
            onst:-1,
            yeson:-1,
            yeson2:-1,
            yeson3:-1,
            yeson4:-1,
            childrenre:[],
             totals:0,
             totals2:0,
             totals3:0,
             pageSize:0,
             screense:false,// true 有搜索条件 false 无搜索条件
             region:[],
             metros:[],
             metross:[],
             cityList:[],
             optionsName:[],
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
                 regions:[],
             },
             datas:[],
             spinShow:true,
             spinShowPoptipsr:true,
             spinShowPoptipsrdata:[]
          }
        },
        mounted(){
            this.datie();
            this.quyu();
            this.ajaxName();//大楼名字
            this.adminname();//大楼名字
            this.datiename();//大楼名字
            this.buildingls(1);//表
        },
        methods:{
          navsr(e){
            this.onst = e
          },
           changseee2(value){
            if (value == undefined) {
               this.screens.brands = '',
               this.buildinglse(1)
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
            console.log(a)
            console.log(this.region[e].children)
          },
          clickyes2(e,a){
            this.yeson2= e
            this.screens.regions[1] = a;
          },
          conno(){
            this.onst = -1
            this.screens.regions = []
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
           changegong(e){
            let query = { id: e};
              this.$router.push({
               name: 'shared_addg',
               query: query
              });
            },
          datiename(){
            let _this = this;
            axios({
                method:'post',
                url:'/api/sharename',
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
             })
            .then(function (res) {
              let data = res.data.message;
              let metros = [];
                for (var i in data) {
                    let nea = {
                       value: data[i],
                       label: data[i]
                      }
                  metros.push(nea)
               }
               _this.metross = metros;
            })
            .catch(function (err) {
                _this.$Notice.error({title: '品牌名字错误'});
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
         adminname(){
          let _this = this;
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
          buildingls(e){
            let _this = this;
             _this.spinShow = true;
            axios({
                method:'post',
                url:'/api/sharelist?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
             })
            .then(function (res) {
              // 2w 3g
              _this.totals = res.data.message.totals; //列表数据
              _this.totals2 = res.data.message.totals2; //列表数据
              _this.totals3 = res.data.message.totals3; //列表数据
              _this.pageSize = res.data.message.pageSize; //每页显示
              _this.datas = res.data.message.data;
              _this.spinShow = false;
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
                url:'/api/sharelist?page='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
                data:{
                  jo:_this.screens
                }
             })
            .then(function (res) {
              _this.totals = res.data.message.totals; //列表数据
              _this.totals2 = res.data.message.totals2; //列表数据
              _this.totals3 = res.data.message.totals3; //列表数据
              _this.pageSize = res.data.message.pageSize; //每页显示
              _this.datas = res.data.message.data;
              _this.spinShow = false;
            })
            .catch(function (err) {
                _this.$Notice.error({title: '类表错误'});
            })
          },
          screenss(){
              this.onst = -1
              this.spinShow = true;
              this.screense = true; //有搜索条件
              this.buildinglse(1);
            },
          reson(){
              this.onst = -1
              this.spinShow = true;
              this.screense = false; //wu搜索条件
              this.screens = {regions:[]}
              this.buildingls(1)
          },
          changepage(page) {
              //翻页
              this.spinShow = true;
              if(this.screense) {
                this.buildinglse(page)
              }else{
                this.buildingls(page); //无
              }
            },
         addLOUPan(){
           this.$router.push({
             name: 'shared_add'
            });
         },
         sharedaddst(e){
          let query = {id: e};
           this.$router.push({
             name: 'sharedadd_st',
             query:query
            });
         },
         lookgong(e,a,q){
           let query = {id: e,ofid:a,uniqidof:q};
           this.$router.push({
             name: 'shared_look',
             query:query
            });
         },
         Poptipsr(e,a){
          this.spinShowPoptipsr = true
          this.spinShowPoptipsrdata = []
           if (a == 0) {
            this.spinShowPoptipsr = false
           }else{
             let _this = this;
              axios({
                method:'post',
                url:'/api/sharelistact?sh2id='+e,
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
             })
            .then(function (res) {
                _this.spinShowPoptipsrdata = res.data.message
                _this.spinShowPoptipsr = false
            })
            .catch(function (err) {
                _this.$Notice.error({title: '工位错误'});
            })

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

