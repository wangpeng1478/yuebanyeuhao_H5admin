<style lang="less">
.visiteVolume3{
.Card2{
    margin: 5px 0;
   .ivu-card-body{
    padding:5px;
    .ivu-form-item{
      width:100%;
      margin:3px 0;
    }
   }
  }
  .Card23{
     .ivu-card-body{
      background:#eee;
      padding:0;
     }
  }
  .cardlist{
    margin:5px 0;
    background:#fff;
    padding: 5px 0 0 0;
    p{
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      padding-left: 16px;
      color: #38435d;
      position:relative;
      .ivu-icon{
        position:absolute;
        position: absolute;
        right: 10px;
        top: 3px;
        color: #38435d;
      }
    }
    .ok{
      color: #a7a7a7;
      .ivu-icon{
        color: #a7a7a7;
      }
    }
    .ivu-row{
      padding: 5px 0;
      .butse{
        text-align:center;
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
    .demo-tabs-style2 > .ivu-tabs.ivu-tabs-card > .ivu-tabs-bar .ivu-tabs-tab{
        border-radius: 0;
        background: #fff;
    }
    .demo-tabs-style2 > .ivu-tabs.ivu-tabs-card > .ivu-tabs-bar .ivu-tabs-tab-active{
        border-top: 1px solid #3399ff;
    }
    .demo-tabs-style2 > .ivu-tabs.ivu-tabs-card > .ivu-tabs-bar .ivu-tabs-tab-active:before{
        content: '';
        display: block;
        width: 100%;
        height: 1px;
        background: #3399ff;
        position: absolute;
        top: 0;
        left: 0;
    }
       .pages{
     float: right;
     margin: 15px 5px 5px 0;
   }
   .sessf{
    position: absolute;
    top: 3px;
    right: 5px;
   }
   .clickbody{
     a{
        &:hover{
            text-decoration: underline;
        }
     }
     .ivu-card-body{
        position:relative;
     }
   }
   .zhuseHtml{
     width:100%;
     margin:0 auto;
     overflow:auto;
     padding-bottom:150px;
     .hr{
       height: 1px;
       border-bottom: 1px dashed #495060;
       margin:15px 0;
    }
   }
   .carclick{
        position:fixed;
        top:41px;
        left:0;
        width:100%;
        height: 100vh;
        overflow: auto;
        z-index: 100;
        .esfan{
            font-weight:100;
            font-size:12px;
            cursor: pointer;
            float:left;
            i{
                margin: 0 5px;
                font-size: 20px;
                vertical-align: top;
                 -webkit-transition:all 0.25s ease-out;
                 transition:all 0.25s ease-out;
            }
            &:hover{
                opacity: 0.6;
            }
        }
         .esfans{
            font-weight:100;
            font-size:12px;
            cursor: pointer;
            float:right;
            i{
                margin: 0 5px;
                font-size: 20px;
                vertical-align: top;
                 -webkit-transition:all 0.25s ease-out;
                 transition:all 0.25s ease-out;
            }
            &:hover{
                opacity: 0.6;
            }
        }
      .bg_bu{
          p{
            margin:5px 0;
           span{
            font-weight:600;
          } 
        }
        
      }


     }

     }
    div .mce-edit-area iframe{
     height:200px !important; 
    }
    .mce-menubar{display:none !important;}
</style>

<template>
<div>
   <Row class="visiteVolume3" :class="{hide:ovhide}">
   <pre>{{searchFole}}</pre>
   <pre>{{access}}</pre>
   <pre>{{historyData}}</pre>
       <Col :xs="24" :sm="24" :md="24" :lg="24" class="searchFoleb">
        <Card class="Card2">
            <Form :model="searchFole" inline>
                <FormItem>
                  <Cascader class="caca" :data="followupdata" v-model="searchFole.cacaDer" placeholder="部门/人员" change-on-select></Cascader>
                </FormItem>
               <!--  <FormItem label="时间" style="margin-bottom:0">
                  <DatePicker v-model="searchFole.time" :options="options2" class="cacas" type="daterange" placement="bottom-end" placeholder="时间"></DatePicker>
                </FormItem> -->
             </Form>
            <!--  <Button @click="sessf" class='sessf' type="primary" shape="circle" icon="paper-airplane">发送工作总结</Button>
                <Modal v-model="modal" width="600">
                    <p slot="header" style="text-align:center">
                        <span>发送工作总结 {{time}}</span>
                    </p>
                    <summ-Ary></summ-Ary>
                    <div slot="footer">
                         <Button :loading="footerlo"  @click="footerYes" type="primary">
                             <span v-if="!footerlo">发送</span>
                              <span v-else>发送中...</span>
                         </Button>
                         <Button  @click="footerNo" type="text">取消</Button>
                    </div>
                </Modal> -->
        </Card>
         <Card class="Card2">
          <p>共{{totals}}条</p>
             <Button @click="sessf" size="small" class='sessf' type="primary" shape="circle" icon="paper-airplane">发送工作总结</Button>
                <Modal v-model="modal" :styles="{top: '5px'}">
                    <p slot="header" style="text-align:center">
                        <span>发送工作总结 {{time}}</span>
                    </p>
                    <summ-Ary></summ-Ary>
                     <!-- setContent -->
                     <!-- <Input v-model="setContent" type="textarea" :rows="4" placeholder="请输入..."></Input> -->
                    <div slot="footer">
                         <Button :loading="footerlo"  @click="footerYes" type="primary">
                              <span v-if="!footerlo">发送</span>
                              <span v-else>发送中...</span>
                         </Button>
                         <Button  @click="footerNo" type="text">取消</Button>
                    </div>
                </Modal>
        </Card>
        </Col>
         <Col :xs="24" :sm="24" :md="24" :lg="24">
            <Card class="Card2 Card23">
            	<p slot="title">
		            <Icon type="ios-calendar-outline"></Icon>
		            工作总结
		        </p>
		        <a href="#" slot="extra" @click.prevent="changeLimit(1)">
		            <Icon type="ios-loop-strong"></Icon>
		            刷新
		        </a>
                <div class="demo-tabs-style2">
                  <Tabs type="card" :value="searchFole.Tabs" :animated="false" @on-click="TabsQ" v-if="access" style="margin-bottom:-5px;margin-left: -1px;">
                    <TabPane label="发件箱"></TabPane>
                    <TabPane label="收件箱"></TabPane>
                  </Tabs>

                 <div class="cf">
                <div class="cardlist" v-for="(item,index) in historyData" :key="index">
                   <Row>
                    <Col span="24">
                        <p @click="lookser(item.id,index,item.title)" :class="{ok:item.action == '已读'}">{{item.title}} <Icon type="ios-arrow-right"></Icon></p>
                    </Col>
                   </Row>
                </div>
                 <div v-if="historyData.length == 0" class="cardlistno">
                 <Icon type="sad-outline"></Icon>
                  <p>没有数据</p>
               </div>
               <Row style="background: #fff">
                  <Col>
                   <Page class="cf pages" :total="totals" :page-size="pageSize"  @on-change="changepage" size="small"></Page>
                  </Col>
               </Row>
               <Spin size="large" fix v-if="loading"></Spin>
              </div> 

                <!-- <div class="cf clickbody">
                    <Table height="550" 
                    :loading="loading" 
                    ref="currentRowTable" 
                    :columns="columns" 
                    :data="historyData" 
                    stripe></Table>

                    <Page class="cf pages" 
                    :total="totals" 
                    :page-size="pageSize"  
                    @on-change="changepage" 
                    show-total></Page>
               </div> -->
                </div>
            </Card>
             <Card v-if='clickbody' class="carclick" :bordered="false">
                        <p slot="title" style="text-align: center;"> 
                        <span @click="clickbodys" class="esfan"><Icon type="ios-arrow-left"></Icon>返回</span> 
                        <span @click="clickbodys" class="esfans"><Icon type="ios-close-empty"></Icon></span> 
                         {{zhuse}}
                        </p>
                        <p>
                         <div class='zhuseHtml'>
                            <div class="bg_bu">
                              <p><span>发信人:</span>{{particular.addresser}}</p>
                              <!-- <p><span>收件人:</span>{{particular.recipients}}</p> -->
                              <p><span>创建日期:</span>{{particular.time}}</p>
                            </div>
                           <div class="hr"></div>
                           <div v-html='particular.content'></div>
                           <Spin v-if="spinShows" fix><span>加载中</span></Spin>
                        </div>
                        </p>
                    </Card>
         </Col>
    </Row>
</div>
</template>

<script>
import tinymce from 'tinymce';
import dataTime from '../../../localStorage/format';
import summAry from './summary/summary.vue';

import axios from 'axios'
import Cookies from 'js-cookie';
export default {
    name: 'visiteVolume3',
    components:{
        summAry
    },
    data() {
    	return {
    		 time: new Date().toLocaleString(),
         ovhide:false,
             searchFole:{
                cacaDer:[],
                time:[ "",""],
                Tabs:0
             },
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
             followupdata: [{
                    value: '错误',
                    label: '错误'
                }],
            loading: true,
            totals: 50,
            pageSize: 20,
            columns: [
                {
                    title: '主题',
                    key: 'zhu',
                    render: (h, params) => {
                       return h('a', {
                         on: {
                            click: () => {
                               this.zhuse = params.row.title;
                               params.row.action = '已读';
                               this.clickbody = true;
                               this.lookc(params.row.id)
                            }
                          }
                    }, params.row.title);
                    }
                },
                {
                    title: '发信人',
                    width: 150,
                    key: 'addressee'
                },
                {
                    title: '发送时间',
                    key: 'time',
                },
                {
                    title: '状态',
                    align: 'center',
                    width: 250,
                    render: (h, params) => {
                       const text = params.row.action ? '未读':'已读';
                       const color = params.row.action =='已读' ? '#e1dedd':'#2d8cf0';
                        return h('Tag', {
                            props: {
                                type: 'dot',
                                color: color
                            },
                             style: {
                                    marginRight: '-20px'
                                },
                        }, params.row.action);
                    }
                }
            ],
            historyData: [],
            modal1: false,
            clickbody:false,
            spinShows:true,
            modal:false,
            footerlo:false,
            zhuse:'',
            access:false,
            setContent:'',
            particular:{
              addresser:'', //发
              recipients:'', //收
              time:'',
              content:''
            }
    	}
    },
    mounted (){
         this.adminname();
         this.accesse();
    },
    methods:{
         lookser(e,a,c){
          this.ovhide = true;
          this.historyData[a].action = '已读'
          this.zhuse = c
          this.clickbody = true;
          this.clickbody = true;
          this.lookc(e)
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
              _this.access = res.data.power.summ02;
              console.log(res.data.power.summ02)
              if (_this.access) {
                 _this.searchFole.Tabs = 1
                 _this.changeLimit(1)
              }else{
                 _this.changeLimit(1)
              }
          })
          .catch(function(err) {
              _this.$Notice.error({ title: '权限获取错误' });
          })
      },
        adminname(){
           let _this = this;
            axios({
                method:'post',
                url:'/api/adminname2x',
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
             })
            .then(function (res) {
              if (res.data.statusx == 200) {
               _this.followupdata = res.data.message
              }else{
                _this.$Notice.error({title: '人员错误'});
              }
            })
            .catch(function (err) {
                _this.$Notice.error({title: '人员错误'});
            })
         },
         changeLimit(e) {
            var _this = this;
              _this.loading = true
               axios({
                    method: 'post',
                    url: '/api/summlist?page='+e,
                    headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                    data:{
                        jo:_this.searchFole
                    }
                })
                .then(function(res) {
                    // console.log(res.data.message.data)
                     _this.historyData = res.data.message.data
                     _this.totals = res.data.message.totals
                     _this.pageSize = res.data.message.pageSize
                     _this.loading = false
                })
                .catch(function(err) {
                    _this.$Notice.error({ title: '错误' });
                })
        },
        TabsQ (e){
         this.searchFole.Tabs =e
        },
         changepage(page) {
            this.changeLimit(page)   
         },
            sessf(){
              this.modal = true;
            },
            clickbodys(){
                 this.ovhide = false
                 this.clickbody = false;
                 this.spinShows = true;
            },
            lookc(e){
               this.spinShows = true;           
                let _this = this;
                 axios({
                    method:'post',
                    url:'/api/summup1?id='+e,
                    headers:{Authorization:'Bearer '+Cookies.set('keya')},
                 })
                .then(function (res) {
                  // console.log(res.data.message)
                  _this.particular =res.data.message
                  _this.spinShows = false;
                })
                .catch(function (err) {
                    _this.$Notice.error({title: '查看失败'});
                })

            },
            footerYes(){
              if(tinyMCE.activeEditor.getContent() == ''){
                 this.$Message.warning('不能为空');
              }else{
              this.footerlo = true; 
               console.log(tinymce.get('tinymceEditer').getContent())
                let _this = this;
                axios({
                    method:'post',
                    url:'/api/summadd',
                    headers:{Authorization:'Bearer '+Cookies.set('keya')},
                    data:{
                        jo:tinymce.get('tinymceEditer').getContent()
                    }
                 })
                .then(function (res) {
                   _this.$Message.success('工作总结发送成功');
                   tinymce.get('tinymceEditer').setContent('')
                   _this.footerlo = false; 
                   _this.modal = false;
                })
                .catch(function (err) {
                    _this.$Notice.error({title: '工作总结发送失败'});
                })

              }
            },
            footerNo(){
              this.setContent = ''
              this.modal = false
              this.footerlo = false; 
            }
    },
     watch: {
        searchFole: {
            handler: function(val, oldVal) {
               this.changeLimit(1)
            },
            deep: true
        },
    }
};
</script>
