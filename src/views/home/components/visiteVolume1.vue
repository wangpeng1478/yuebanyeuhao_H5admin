<style lang="less">
// scoped
.visiteVolume1{
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
      padding-top: 2.5px;
      .butse{
        text-align:center;
        line-height: 40px;
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
 <div class="visiteVolume1">
 	  <Col :xs="24" :sm="24" :md="24" :lg="24" class="searchFolebs">
     <pre>{{historyData}}</pre>
     <pre>{{screens}}</pre>
     <pre>{{bo1}}</pre>
     <pre>{{bo2}}</pre>
        <Card class="Card2">
            <Form :model="screens" label-position="right" inline>
                <FormItem>
                    <!--  <Select size="small" v-model="screens.luru" clearable filterable placeholder="人员">
                        <Option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                     </Select> -->
                     <select v-model="screens.luru" class="selectUI">
                       <option value='' disabled selected style='display:none;'>人员</option>
                       <option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</option>   
                     </select>
                </FormItem>
                 <FormItem>
                    <RadioGroup v-model="screens.type" type="button">
                      <Radio label="全部"></Radio>
                      <Radio label="待审核"></Radio>
                      <Radio label="已拒绝"></Radio>
                      <Radio label="已通过"></Radio>
                  </RadioGroup>
                </FormItem>
             </Form>
        </Card>

          <Card class="Card2 Card23">
            <p slot="title">
                <Icon type="ios-eye-outline" size="20" style="vertical-align: top;"></Icon>
               隐藏联系人
            </p>
            <a href="#" slot="extra" @click.prevent="fangyuaData(1)">
                <Icon type="ios-loop-strong"></Icon>
                刷新
            </a>
             <div class="cf">

             <div class="cardlist" v-for="(item,index) in historyData" :key="index">
               <p style="color:#495060">{{item.shen}} {{item.lei? '申请隐藏' : '取消隐藏'}} “{{item.xin}}” 联系人</p>
               <p>
               {{item.time}}
               <span class="tis" :class="{'blues': !item.tongguo ? !item.jujue  ? false : true : item.tongguo? false : false}">
               {{!item.tongguo ? !item.jujue  ? '待审核' : '已拒绝' : item.tongguo? '已通过' : ''}}
               </span>
               </p>
               <Row>
                  <Col span="16">
                      <p>原因:{{item.yuan}}</p>
                      <p>备注:{{item.bei}}</p>
                  </Col>
                  <Col span="8" class="butse">
                     <Button type="primary" size="small" 
                     :disabled="!item.tongguo ? item.jujue  ? true : false : item.tongguo? true : false"
                     :style="{display:bo1}" @click="yesok(item.id)">
                       {{!item.tongguo ? "通过":"已通过"}}
                     </Button> 
                     <Button type="error" size="small" 
                     :disabled="!item.tongguo ? item.jujue  ? true : false : item.tongguo? true : false"
                     :style="{display:bo1}" @click="modal1 = true,id = item.id">
                       {{!item.jujue ? "拒绝":"已拒绝"}}
                     </Button> 
                      <Button type="error" size="small" 
                     :style="{display:bo2}">
                       取消
                     </Button> 
                  </Col>
              </Row>
             </div>
             <div v-if="historyData.length == 0" class="cardlistno">
               <Icon type="sad-outline"></Icon>
                <p>没有数据</p>
             </div>
             <Spin size="large" fix v-if="loading"></Spin>
            <Page class="cf pages" :total="totals" :page-size="pageSize"  @on-change="changepage" size="small"></Page>
    			   <!--  <Table height="550" :loading="loading" highlight-row ref="currentRowTable" :columns="columns" :data="historyData" stripe></Table>
    			    <Page class="cf pages" :total="totals" :page-size="pageSize"  @on-change="changepage" show-total></Page> -->
    			 </div>
            <Modal
              v-model="modal1"
              :styles="{top: '5px'}"
              title="拒绝理由">
              <Input v-model="showt" type="textarea" :rows="4" placeholder="拒绝理由..."></Input>
               <div slot="footer">
                  <Button type="primary" @click="oks" :loading="loading2">确定</Button>
                  <Button type="dashed" @click="modal1 = false">取消</Button>
              </div>
          </Modal>

          </Card>
        </Col>
 </div>
</template>

<script>

import axios from 'axios'
import Cookies from 'js-cookie';

 export default {
    	name: 'visiteVolume1',
        data () {
            return {
              id:'0',
              bo1:JSON.parse(Cookies.set('auth')).ente07 ? 'inline-block':'none',
              bo2:!JSON.parse(Cookies.set('auth')).ente07 ? 'inline-block':'none',
              loading: true,
            	loading2: false,
            	totals: 50, //共多少条数据
            	pageSize: 10, //显示多少
              modal1:false,
              showt:'',
              screens:{
                type: "全部",
                luru: ""
              },
              cityList:[],
                columns: [
                    {
                        title: '联系人',
                        key: 'xin'
                    },
                    {
                        title: '类型',
                        align: 'center',
                        key: 'lei',
                        render: (h, params) => {
                         	const text = params.row.lei ? '申请隐藏' : '取消隐藏';
                         	const color = params.row.lei ? 'blue' : 'red';
                         	return h('Tag', {
                                props: {
                                    type: 'dot',
                                    color: color
                                }
                            }, text);
                         }
                    },
                    {
                        title: '申请人',
                        align: 'center',
                        key: 'shen'
                    },
                    {
                        title: '申请时间',
                        align: 'center',
                        key: 'time'
                    },
                     {
                        title: '原因',
                        align: 'center',
                        key: 'yuan'
                    },
                     {
                        title: '备注',
                        align: 'center',
                        key: 'bei'
                    },
                     {
                        title: '状态',
                        align: 'center',
                        render: (h, params) => {
                            // console.log(params)
                          const text = !params.row.tongguo ? !params.row.jujue  ? '待审核' : '已拒绝' : params.row.tongguo? '已通过' : '';
                         	const color = !params.row.tongguo ? params.row.jujue  ? 'red' : '' : params.row.tongguo? 'blue' : '';
                         	return h('Tag', {
                                props: {
                                    type: 'dot',
                                    color: color
                                }
                            }, text);
                         }
                    },
                    {
                        title: '操作',
                        align: 'center',
                        key: 'action',
                        width: 180,
                        render: (h, params) => {
                        
                        const disa = !params.row.tongguo ? params.row.jujue  ? true : false : params.row.tongguo? true : false;
                        	let to = () =>{
                        	 if (!params.row.tongguo) {
                               return '通过'
                        	  }else{
                        	   return '已通过'
                        	  }
                        	}
                        	let ju = () =>{
                        	 if (!params.row.jujue) {
                             return '拒绝'
                        	  }else{
                        	   return '已拒绝'
                        	  }
                        	}
                          // display: block;
                          let cu = JSON.parse(Cookies.set('auth')).ente07
                          const bo1  = cu ? 'inline-block':'none'
                          const bo2  = !cu ? 'inline-block':'none'
                          // console.log(bo1)
                            return h('div', [
                                h('Button', {
                                    props: {
                                        type: 'primary',
                                        size: 'small',
                                        disabled: disa
                                    },
                                    style: {
                                        marginRight: '5px',
                                        display:bo1,
                                    },
                                    on: {
                                        click: () => {
                                            //通过
                                            // params.row.tongguo = true;
                                            this.id = params.row.id;
                                            this.yesok();
                                        }
                                    }
                                }, to()),
                                 h('Button', {
                                    props: {
                                        type: 'error',
                                        size: 'small',
                                        disabled: disa
                                    },
                                     style: {
                                        display:bo1,
                                    },
                                    on: {
                                        click: () => {
                                           // params.row.jujue = true;
                                          this.id = params.row.id;
                                          this.modal1 = true
                                        }
                                    }
                                }, ju()),
                                 h('Button', {
                                    props: {
                                        type: 'error',
                                        size: 'small',
                                    },
                                     style: {
                                        display:bo2,
                                    },
                                    on: {
                                        click: () => {
                                           // params.row.jujue = true;
                                          this.id = params.row.id;
                                          this.noook()
                                        }
                                    }
                                }, '取消申请')
                            ]);
                        }
                    }
                ],
                historyData: []
            }
        },
        mounted(){
           this.adminname();
           this.fangyuaData(1);
        },
        methods:{
              adminname() {
                let _this = this;
                axios({
                        method: 'post',
                        url: '/api/adminname3',
                        headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                    })
                    .then(function(res) {
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
                    .catch(function(err) {
                        _this.$Notice.error({ title: '人员错误' });
                    })
            },
            fangyuaData(e){
                  this.loading = true;
                  let _this = this;
                   axios({
                        method: 'post',
                        url: '/api/suzulist?page=' + e,
                        headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                        data:{
                          jo:_this.screens
                        }
                    })
                    .then(function(res){
                       // console.log(res.data.message.data)
                       _this.historyData = res.data.message.data;
                       _this.totals = res.data.message.totals
                       _this.pageSize =res.data.message.pageSize
                       _this.loading = false;
                    })
                    .catch(function(err) {
                        _this.$Notice.error({ title: '错误' });
                    })
            },
            changepage(page) {
              this.fangyuaData(page)
            },
            yesok(e){
                  let _this = this;
                   axios({
                        method: 'post',
                        url: '/api/suzuadopt1?id=' + e,
                        headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                    })
                    .then(function(res) {
                         // console.log(res)
                        _this.$Message.success('已通过');
                       _this.fangyuaData(1);
                    })
                    .catch(function(err) {
                        _this.$Notice.error({ title: '错误' });
                    })
            },
            noook(){
                  let _this = this;
                   axios({
                        method: 'post',
                        url: '/api/suzuadopt3?id=' + _this.id,
                        headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                    })
                    .then(function(res) {
                         // console.log(res)
                        _this.$Message.success('已取消');
                       _this.fangyuaData(1);
                    })
                    .catch(function(err) {
                        _this.$Notice.error({ title: '错误' });
                    })
            },
            oks(){
              if (this.showt !=='') {
                  this.loading2 = true;
                   let _this = this;
                   axios({
                        method: 'post',
                        url: '/api/suzuadopt2',
                        headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                        data:{
                          'jo':{
                            id:_this.id,
                            rema2:_this.showt
                          }
                        }
                    })
                    .then(function(res) {
                       _this.$Message.success('已拒绝');
                       _this.fangyuaData(1);
                       _this.showt = ''
                       _this.modal1 = false
                       _this.loading2 = false
                    })
                    .catch(function(err) {
                        _this.$Notice.error({ title: '错误' });
                    })
              }
            }
        },
        watch: {
          screens: {
              handler: function(val, oldVal) {
                 this.fangyuaData(1);
              },
              deep: true
          },
      }
    }

</script>
