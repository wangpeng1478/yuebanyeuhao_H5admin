<style lang="less">
.Tabss {
    .ivu-card-body {
        padding: 5px;
        padding-bottom: 0;
        padding-top: 0;
    }

    .ivu-tabs-bar {
        margin: 0;
        border-bottom: 1px solid #ffffff;
    }
    .ivu-tabs-nav {
        padding: 5px 0;
    }
    .righeS {
        position: absolute;
        display: block;
        top: 0;
        right: 0;
        height: 100%;
        line-height: 46px;
        .funnel {
            cursor: pointer;
            &:hover {
                opacity: 0.7;
            }
        }
        .sessf {
            margin: 0 20px;
        }
        .ons {
            color: #2d8cf0;
        }
    }
}

.Cardfun {
    .ivu-card-body {
        padding: 0;
        .ivu-form-item {
            margin-bottom: 0;
            margin: 8px 0;
        }
    }
}

.Deal {
    .ivu-card {
        margin-bottom: 5px;
    }
    .pages {
        text-align: right;
        margin: 15px 0;
        padding-bottom: 100px;
    }
     .cars{
        .ivu-card-body{
            padding:7px;
        }
        .le{
            float:left;
            line-height: 25px;
            padding-left:10px;
        }
        .sessf{
            float:right;
        }
    }
    .list {
        list-style-type: none;
        .li {
            border: 1px solid #e6e6e6;
            border-bottom: none;
            transition: all 0.3s ease-out;
            padding: 10px;
            &:hover {
                background-color: #f2fafe;
            }
            &:last-child {
                border-bottom: 1px solid #e6e6e6;
            }
            .li1 {
                padding: 5px;
                h2 {
                    margin: 5px 0;
                    overflow: hidden;
                    white-space: nowrap;
                    text-overflow: ellipsis;
                        font-size: 1.1em;
                    a {
                        color: #495060;
                    }
                }
                span {
                    margin: 3px 0;
                    padding-left: 10px;
                }
            }
            .li2 {
                span {
                    padding: 5px;
                    line-height: 70px;
                    overflow: hidden;
                    white-space: nowrap;
                    text-overflow: ellipsis;
                    padding-left: 15px;
                }
            }
            .li3 {
                padding: 5px;
                padding-right: 20px;
                height: 100%;
                text-align: right;
                padding-top: 10px;
                .buttose {
                    color: #dd514c;
                    background-color: transparent;
                    background-image: none;
                    border-color: #dd514c;
                    padding: 3px 5px;
                    font-size: 12px;
                    cursor: pointer;
                    border: 1px solid #dd514c;
                    border-radius: 3px;
                }
                .buttoseyes {
                    color: #c4c4c4;
                    border-color: #c4c4c4;
                }
                .buttoseyese {
                    color: #FF9800;
                    border-color: #FF9800;

                }
                .time {
                    display: block;
                    margin-top: 10px;
                    font-size:12px;
                }
                .ivu-timeline-item-content {
                    padding: 1px 1px 0 24px
                }
            }
        }
    }
}
</style>
<template>
    <div class="Deal">
        <pre>{{searchFole}}</pre>
        <Row>
            <Col :xs="24" :sm="24" :md="24" :lg="24">
            <Card class='Tabss'>
                <Tabs value="1" :animated="false" @on-click="TabsVis">
                    <TabPane name="0" label="全部报告"></TabPane>
                    <TabPane name="1" label="待确认"></TabPane>
                    <TabPane name="2" label="已完成"></TabPane>
                </Tabs>
            </Card>
            <Card class="Cardfun" style="padding:0 5px;">
                <Form :model="searchFole">
                    <FormItem>
                        <Cascader class="caca" :data="cacaDer" v-model="searchFole.cacaDer" placeholder="部门/人员" change-on-select></Cascader>
                    </FormItem>
                   <!--  <FormItem label="时间">
                        <DatePicker v-model="searchFole.time" class="cacas" :options="options2" type="daterange" placement="bottom-end" placeholder="时间"></DatePicker>
                    </FormItem> -->
                </Form>
            </Card>
            <Card class="cars">
            <div class="cf">
                <p class="le">共{{totals}}条</p>
                <Button @click='addDeal' class='sessf' type="primary" size="small" shape="circle" icon="plus">新增成交报告</Button>
            </div>
            </Card>
            </Col>
            <Col :xs="24" :sm="24" :md="24" :lg="24">
            <Card class='cf'>
                <p slot="title">
                    <Icon type="ios-list-outline"></Icon>
                    成交报告列表
                </p>
                <a href="#" slot="extra" @click.prevent="changeLimit(1)">
                    <Icon type="ios-loop-strong"></Icon>
                    刷新
                </a>
                <ul class="list cf">
                    <li class="li cf" v-for="item in Sdatd" :key="item.length">
                    <Row>
                        <Col class='li1 cf' :xs="18" :sm="18" :md="18" :lg="18">
                            <h2>
                              <a :title='item.name' href="#" @click.prevent="Dealkan(item.id)" >{{item.name}}</a>
                            </h2>
                            <span :title='item.id'>ID:{{item.id}}</span>
                            <span :title="item.time">{{item.time}}</span>
                        </Col>
                       <!--  <Col class='li2 cf' :xs="12" :sm="6" :md="6" :lg="6">
                           <span :title="item.Remarks">{{item.Remarks}}</span>
                        </Col> -->
                        <Col class='li3 cf' :xs="6" :sm="6" :md="6" :lg="6">
                        <Poptip trigger="hover" placement="left-start">
                            <!-- <span :class="{ buttoseyes: !item.ok }" class='buttose'>{{item.ok ?'待确认':'已完成'}}</span> -->
                            <span :class="{ buttoseyes: item.ok =='已完成',buttoseyese: item.ok =='请修改' }" class='buttose'>{{item.ok}}</span>
                            <div style="text-align:center" slot="content">
                                <Timeline>
                                    <TimelineItem :color="item.Timeline[0] ?'#dd514c':'#c4c4c4'">
                                        <span :style="item.Timeline[0] ?'color:#dd514c':'color:#c4c4c4'">业务合作人确认</span>
                                    </TimelineItem>
                                    <TimelineItem :color="item.Timeline[1] ?'#dd514c':'#c4c4c4'">
                                        <span :style="item.Timeline[1] ?'color:#dd514c':'color:#c4c4c4'">房源归属人确认</span>
                                    </TimelineItem>
                                    <TimelineItem :color="item.Timeline[2] ?'#dd514c':'#c4c4c4'">
                                        <span :style="item.Timeline[2] ?'color:#dd514c':'color:#c4c4c4'">照片归属人确认</span>
                                    </TimelineItem>
                                    <TimelineItem :color="item.Timeline[3] ?'#dd514c':'#c4c4c4'">
                                        <span :style="item.Timeline[3] ?'color:#dd514c':'color:#c4c4c4'">经理确认</span>
                                    </TimelineItem>
                                    <TimelineItem :color="item.Timeline[4] ?'#dd514c':'#c4c4c4'">
                                        <span :style="item.Timeline[4] ?'color:#dd514c':'color:#c4c4c4'">行政确认</span>
                                    </TimelineItem>
                                    <TimelineItem :color="item.Timeline[5] ?'#dd514c':'#c4c4c4'">
                                        <span :style="item.Timeline[5] ?'color:#dd514c':'color:#c4c4c4'">财务确认</span>
                                    </TimelineItem>
                                    <TimelineItem :color="item.Timeline[6] ?'#dd514c':'#c4c4c4'">
                                        <span :style="item.Timeline[6] ?'color:#dd514c':'color:#c4c4c4'">总经理确认</span>
                                    </TimelineItem>
                                </Timeline>
                            </div>
                        </Poptip>
                        </Col>
                        </Row>
                    </li>
                    <li v-if="Sdatd.length ==0" style="text-align:center"><h2>没有找到</h2></li>
                </ul>
                <Page class="cf pages" :total="totals" :page-size="pageSize" @on-change="changepage" size="small"></Page>
                <Spin size="large" fix v-if="loading"></Spin>
            </Card>
            </Col>
        </Row>
    </div>
</template>
<script>
import axios from 'axios'
import Cookies from 'js-cookie';

export default {
    name: 'Deal',
    data() {
        return {
            time: new Date().toLocaleString(),
            options2: {
                shortcuts: [{
                        text: '一周',
                        value() {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
                            return [start, end];
                        }
                    },
                    {
                        text: '一个月',
                        value() {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
                            return [start, end];
                        }
                    },
                    {
                        text: '三个月',
                        value() {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
                            return [start, end];
                        }
                    }
                ]
            },
            TabsData: 0,
            totals: 0,
            pageSize: 0,
            searchFole: {
                TabPane: '1',
                cacaDer: [],
                time: ["", ""]
            },
            cacaDer: [],
            funnelss: true,
            loading: true,
            Sdatd: []
        };
    },
    mounted() {
        this.adminname();
        this.adminname();
        this.changeLimit(1);
    },
    methods: {
        adminname() {
            let _this = this;
            axios({
                    method: 'post',
                    url: '/api/adminname2',
                    headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                })
                .then(function(res) {
                    if (res.data.statusx == 200) {
                        _this.cacaDer = res.data.message
                    } else {
                        _this.$Notice.error({ title: '人员错误' });
                    }
                })
                .catch(function(err) {
                    _this.$Notice.error({ title: '人员错误' });
                })
        },
        TabsVis(e) {
            this.searchFole.TabPane = e
        },
        funnels() {
            this.funnelss = !this.funnelss
        },
        changeLimit(e) {
            var _this = this;
              _this.loading = true
               axios({
                    method: 'post',
                    url: '/api/deallist?page='+e,
                    headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
                    data:{
                        jo:_this.searchFole
                    }
                })
                .then(function(res) {
                    // console.log(res.data.message.data)
                     _this.Sdatd = res.data.message.data
                     _this.totals = res.data.message.totals
                     _this.pageSize = res.data.message.pageSize
                     _this.loading = false
                })
                .catch(function(err) {
                    _this.$Notice.error({ title: '类表错误' });
                })


        },
        changepage(page) {
            this.changeLimit(page);
        },
        addDeal(){
            this.$router.push({
                name: 'Deal_add'
            });
        },
        Dealkan(e) {
        let query = { deal_id: e };
        this.$router.push({
            name: 'Deal_Looke',
            query: query
        });
        }
    },
    watch: {
        searchFole: {
            handler: function(val, oldVal) {
                this.changeLimit(1);
            },
            deep: true
        },
    }
};
</script>