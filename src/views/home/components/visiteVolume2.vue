<style lang="less">
  .visiteVolume2{
    input[type="date"]{
      width: 100%;
      line-height: 32px;
    }
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
  .cardlist{
    margin:5px 0;
    background:#fff;
    padding: 5px 0 0 0;
    p{
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      padding-left: 16px;
      color: #777;
      .tis{
        display: inline-block;
        border: 1px solid #2d8cf0;
        padding: 2px;
        font-size: 11px;
        color: #2d8cf0;
        transform: scale(0.7);
        vertical-align: unset;
      }
      .blues{
        border: 1px solid #ed3f14;
        color: #ed3f14;
      }
    }
    .ivu-row{
      border-top: 1px solid #eee;
      margin-top: 2.5px;
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
  .pages{
    background:#fff;
    text-align:right;
    padding: 10px;
  }
 }
</style>

<template>
   <div class="visiteVolume2">
    <Col :xs="24" :sm="24" :md="24" :lg="24" class="searchFolebs">
        <Card class="Card2">
          <RadioGroup v-model="RadioGroups" type="button" class="RadioGroups">
            <Radio label="全部"></Radio>
            <Radio label="未读"></Radio>
            <Radio label="已读"></Radio>
            <Radio label="已发送"></Radio>
          </RadioGroup>
        </Card>
          <Card class="Card2 Card23">
              <p slot="title"> 
              <Icon style="vertical-align: top;" size="18" type="ios-bell-outline"></Icon>
              工作提醒
              </p>
               <a href="#" slot="extra" @click.prevent="fangyuaData(1)">
                <Icon type="ios-loop-strong"></Icon>
                刷新
              </a>

              <div class="cf">
                <div class="cardlist" v-for="(item,index) in historyData" :key="index">
                  <p>
                  {{item.fa}} - {{item.time}} - 
                  <span>{{item.type}}</span>
                  </p>
                   <Row>
                  <Col span="20">
                      <p class="p2">{{item.con}}</p>
                  </Col>
                  <Col span="4" class="butse">
                     <Button @click="lookew(item.id)" type="primary" size="small">查看 <Icon type="ios-arrow-right"></Icon></Button> 
                  </Col>
              </Row>
                </div>
                 <div v-if="historyData.length == 0" class="cardlistno">
                 <Icon type="sad-outline"></Icon>
                  <p>没有数据</p>
               </div>
               <Page class="cf pages" :total="totals" :page-size="pageSize"  @on-change="changepage" size="small"></Page>
               <Spin size="large" fix v-if="loading"></Spin>
              </div> 

             <!-- <div class="cf">
                <Table height="350" :loading="loading" highlight-row ref="currentRowTable" :columns="columns" :data="historyData" stripe></Table>
                <Page class="cf pages" :total="totals" :page-size="pageSize"  @on-change="changepage" show-total></Page>
             </div> -->
          </Card>
        </Col>
        <Col :xs="24" :sm="24" :md="24" :lg="24">
            <Card style="margin-bottom:15px;">
            <p slot="title">  <Icon style="vertical-align: top;" size="19" type="ios-bell-outline"></Icon> 添加提醒</p>
             <Forms></Forms>
            </Card>
        </Col>
 </div>
</template>
<script>
import axios from 'axios'
import Cookies from 'js-cookie';
import Forms from './Forms/Forms.vue';
export default {
      name: 'visiteVolume2',
         components: {
           Forms
         },
        data () {
            return {
              loading: true,
              totals: 50, //共多少条数据
              pageSize: 8, //显示多少
              RadioGroups: '全部', //显示多少
                columns: [
                    {
                        title: '收信日期',
                        key: 'time',
                        width: 200,
                    },
                    {
                        title: '发信人',
                        key: 'fa',
                        width: 100,
                    },
                    {
                        title: '内容',
                        key: 'con'
                    },
                    {
                        title: '类型',
                        align: 'center',
                        key: 'type',
                        width: 150,
                        render: (h, params) => {
                          const color = params.row.type == '未读' ? 'red' : params.row.type == '已读' ? '#d8d8d8' : params.row.type == '已发送' ? '#2d8cf0' : '';
                          return h('Tag', {
                                props: {
                                    type: 'dot',
                                    color: color
                                }
                            }, params.row.type);
                         }
                     },
                    {
                        title: '操作',
                        key: 'cao',
                        width: 100,
                        render: (h, params) =>{
                            return h('div', [
                                h('Button', {
                                    props: {
                                        type: 'primary',
                                        size: 'small'
                                    },
                                    style: {
                                        marginRight: '5px'
                                    },
                                    on: {
                                        click: () => {
                                            this.lookke(params.row.id)
                                            let query = { deal_id: params.row.id};
                                            this.$router.push({
                                             name: 'clientadd_look',
                                             query: query
                                            });
                                        }
                                    }
                                }, '查看')
                            ]);
                        }
                    },
                ],
                historyData: []
            }
        },
        mounted(){
           this.fangyuaData(1)
        },
        methods:{
          lookew(e){
             this.lookke(e)
              let query = { deal_id: e};
              this.$router.push({
               name: 'clientadd_look',
               query: query
              });
          },
          fangyuaData(e){
                 this.loading = true;
                  let _this = this;
                   axios({
                        method: 'post',
                        url: '/api/warnlist?page=' + e,
                        headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                        data:{
                          jo:_this.RadioGroups
                        }
                    })
                    .then(function(res) {
                       // console.log(res)
                       _this.$store.commit('setMessageCount', res.data.message.totals2); 
                       _this.historyData = res.data.message.data
                       _this.totals = res.data.message.totals
                       _this.pageSize = res.data.message.pageSize
                       _this.loading = false;
                    })
                    .catch(function(err) {
                        _this.$Notice.error({ title: '错误' });
                    })
          },
          lookke(e){
               let _this = this;
               axios({
                    method: 'post',
                    url: '/api/warnread?id=' + e,
                    headers: { Authorization: 'Bearer ' + Cookies.set('keya') }
                })
                .then(function(res) {
                   console.log(res)
                })
                .catch(function(err) {
                    _this.$Notice.error({ title: '错误' });
                })
          },
          changepage(page) {
            this.fangyuaData(page)
          },
          // onRefresList(){
          //   this.fangyuaData(1)
          // }
        },
        watch:{
           RadioGroups:{
              handler: function (val, oldVal){
               this.fangyuaData(1)
              },
              deep: true
           } 
        }
    }

</script>
