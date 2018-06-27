
<style lang="less">
.visiteVolume0{
    .fangenjine{
     .ivu-card-body{
        padding:0;
        background: #f0f0f0;
        .listfe{
          margin:5px 0;
          border: none;
          padding:5px;
          .ivu-card-body{
            background:#fff;
          }
        }
     }
     .tiie1{
        font-size: 1.1em;
        font-weight:500;
        padding-left: 16px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
     }
     .tiie2{
        padding-left: 16px;
        font-size:11px;
        color: #777;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
     }
     .ivu-row{
        padding-left: 16px;
        font-size:11px;
        color: #777;
     }
     .ivu-col{
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
        color: #777;
     }
    }
    .Card2{
    margin: 5px 0;
   .ivu-card-body{
    padding:5px;
    .ivu-form-item{
      width:100%;
      margin:0;
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
     <Row class="visiteVolume0">
    
     <!-- <pre>{{followupdata}}</pre> -->
       <Col :xs="24" :sm="24" :md="24" :lg="24" class="searchFoleb">
            <Card :style="{margin: '5px 0'}" class="Card2">
                <Form :model="searchFole" label-position="right" inline>
                    <FormItem>
                     <Cascader class="caca" :data="followupdata" v-model="searchFole.cacaDer" placeholder="部门/人员" change-on-select></Cascader>
                    </FormItem>

                    <!-- <FormItem label="时间" style="margin-bottom:0">
                     <DatePicker v-model="searchFole.time" :options="options2" class="cacas" type="daterange" placement="bottom-end" placeholder="时间"></DatePicker>
                    </FormItem> -->
                 </Form>
            </Card>
            <!-- <div class="filter_nav">
                <Row>
                    <Col span="12">
                      <span>部门/人员</span>
                      <Icon type="arrow-down-b"></Icon>
                    </Col>
                    <Col span="12">
                      <span>时间</span>
                      <Icon type="arrow-down-b"></Icon>
                    </Col>
                </Row>
                <div class="filter_con">
                     <Row>
                             <Col span="10" class="filter_contime">
                                <p v-for="(n, index) in followupdata" :key="n.length">{{n.value}}</p>
                             </Col>
                             <Col span="14" class="filter_consr">
                                <p>222</p>
                             </Col>
                         </Row>                                                                       
                </div>
            </div> -->
        </Col>
        <Col :xs="24" :sm="24" :md="24" :lg="24" :style="{margin: '5px 0'}">
            <Card>
                 <p slot="title">
                    <Icon type="ios-clock-outline"></Icon>
                    最近 ({{visite_volume_con.xAxisdata[0]}} 至 {{visite_volume_con.xAxisdata[visite_volume_con.xAxisdata.length - 1]}})
                </p>
                <div style="width:100%;height:300px; margin:0 auto;" id="visite_volume_con"></div>
            </Card> 
            <Spin size="large" fix v-if="loading"><span>加载中</span></Spin> 
        </Col>
         <Col :xs="24" :sm="24" :md="24" :lg="24" :style="{marginBottom: '5px'}">
            <Card>
                <p slot="title">
                    <Icon type="ios-clock-outline"></Icon>
                   总数
                </p>
               <div style="width:100%;height:250px; margin: -50px auto 0 auto;" id="myChart"></div>
            </Card>
            <Spin size="large" fix v-if="loading"><span>加载中</span></Spin> 
        </Col>
      <!-- 表格 -->
       <Col :xs="24" :sm="24" :md="24" :lg="24" class="searchFolebs">
          <Card class="fangenjine">
            <p slot="title">
                <Icon type="ios-clock-outline"></Icon>
               房源跟进
            </p>
             <div class="cf">
                <Card dis-hover v-for="(item, index) in historyData" :key="index" class="listfe">
                    <p class="tiie1">{{item.men}}</p>
                    <p class="tiie2">{{item.gen}} | ID:{{item.id}}</p>
                    <Row>
                        <Col span="20">
                            <p>{{item.time}}</p>
                            <p>{{item.con}}</p>
                        </Col>
                        <Col span="4">
                            <Button @click="rowewpus(item.id)" type="primary" size="small">查看 <Icon type="ios-arrow-right"></Icon></Button>
                        </Col>
                    </Row>
                </Card>
              <div v-if="historyData.length == 0" class="cardlistno">
                  <Icon type="sad-outline"></Icon>
                  <p>没有数据</p>
               </div>
               <!--  <Table height="550" :loading="loading" highlight-row ref="currentRowTable" :columns="columns" :data="historyData" stripe no-filtered-data-text="暂无跟进"></Table> -->
             </div>
          </Card>
        </Col>

      <!-- 表格 -->
      
    </Row>

</template>

<script>
import echarts from 'echarts';
import axios from 'axios'
import Cookies from 'js-cookie';
export default {
    name: 'visiteVolume',
    data () {
        return {
            time: new Date().toLocaleString(),
            searchFole:{
                cacaDer:[],
                time:[]
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
            visite_volume_con:{
                xAxisdata:["09-16", "06-25", "09-23", "07-11", "02-19", "07-12", "09-17"],
                seriesdata:[{
                        name:'录入房源',
                        type:'line',
                        stack: '总量',
                        data:[122, 132, 101, 134, 90, 230, 210]
                    },
                    {
                        name:'房源跟进',
                        type:'line',
                        stack: '总量',
                        data:[220, 182, 191, 234, 290, 330, 310]
                    },
                    {
                        name:'录入客户',
                        type:'line',
                        stack: '总量',
                        data:[150, 232, 201, 154, 190, 330, 410]
                    },
                    {
                        name:'客户跟进',
                        type:'line',
                        stack: '总量',
                        data:[320, 332, 301, 334, 390, 330, 320]
                    },
                    {
                        name:'录入照片',
                        type:'line',
                        stack: '总量',
                        data:[820, 932, 901, 934, 1290, 1330, 1320]
                    }
                ]
            },
            myChart:[5, 20, 36, 10, 10],
            followupdata: [],
            loading: true,
                columns: [
                    {
                        title: '房源ID',
                        key: 'id',
                        width: 100,
                        sortable: true
                    },
                    {
                        title: '门牌号',
                        width: 200,
                        key: 'men'
                    },
                    {
                        title: '跟进人',
                        width: 80,
                        key: 'gen'
                    },
                    {
                        title: '跟进时间',
                        width: 200,
                        key: 'time',
                        sortable: true
                    },
                    {
                        title: '内容',
                        key: 'con'
                    },
                    {
                        title: '操作',
                        key: 'action',
                        width: 150,
                        render: (h, params) => {
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
                                              let query = { deal_id: params.row.id};
                                              this.$router.push({
                                               name: 'house_follow',
                                               query: query
                                              });
                                        }
                                    }
                                }, '查看详细'),
                            ]);
                        }
                    }
                ],
                historyData: []
        };
    },
    mounted () {
      this.adminname();
      this.changeLimit();
    },
    methods:{
      rowewpus(e){
        let query = { deal_id: e};
          this.$router.push({
           name: 'house_follow',
           query: query
          });
      },
      changeLimit(){
          let _this = this;
           _this.loading = true
            axios({
                method:'post',
                url:'/api/calcup1',
                headers:{Authorization:'Bearer '+Cookies.set('keya')},
                data:{
                  jo:_this.searchFole
                }
             })
            .then(function (res) {
                // console.log(res.data.message.outor4)
                _this.visite_volume_con.xAxisdata = res.data.message.xAxisdata
                _this.visite_volume_con.seriesdata = res.data.message.seriesdata
                _this.myChart = res.data.message.myChart
                _this.historyData = res.data.message.outor4
                _this.se();
                _this.drawLine();
                _this.loading = false
            })
            .catch(function (err) {
                // _this.$Notice.error({title: '错误0'});
            })

      },
      adminname(){
           let _this = this;
            axios({
                method:'post',
                url:'/api/adminname2',
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
       se(){
        var _this = this;
          let visiteVolume = echarts.init(document.getElementById('visite_volume_con'));
            const option = {
                tooltip: {
                    trigger: 'axis'
                },
                legend: {
                    data:['录入房源','房源跟进','录入客户','客户跟进','录入照片']
                },
                grid: {
                    left: '5%',
                    right: '5%',
                    bottom: '10%',
                    containLabel: true
                },
                xAxis: {
                    type: 'category',
                    boundaryGap: false,
                    data: _this.visite_volume_con.xAxisdata
                },
                yAxis: {
                    type: 'value'
                },
                series: _this.visite_volume_con.seriesdata
            };
            
            visiteVolume.setOption(option);
            window.addEventListener('resize', function () {
                visiteVolume.resize();
            });
       },
       drawLine(){
        var _this = this;
        let myChart = echarts.init(document.getElementById('myChart'));
        myChart.setOption({
            tooltip: {},
            xAxis: {
                 data:['录入房源','房源跟进','录入客户','客户跟进','录入照片']
            },
            grid: {
                left: '5%',
                right: '5%',
                bottom: '10%',
                containLabel: true
            },
            yAxis: {
                type: 'value'
            },
            series: [{
                name: '销量',
                type: 'bar',
                data: _this.myChart
            }]
        });
        window.addEventListener('resize', function () {
            myChart.resize();
        });
     }
    },
    watch: {
        searchFole: {
            handler: function(val, oldVal) {
               this.changeLimit()
            },
            deep: true
        },
    }
};
</script>
