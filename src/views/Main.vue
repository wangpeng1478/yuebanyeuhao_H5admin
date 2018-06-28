<style lang="less">
    .lock-screen-back{
    border-radius: 50%;
    z-index: -1;
    box-shadow: 0 0 0 0 #667aa6 inset;
    position: fixed;
    left: 50%;
    top: 50%;
    -webkit-transform: translate(-50%,-50%); transform: translate(-50%,-50%);
    // transition: all 3s;
}
.main{
    position: absolute;
    width: 100%;
    height: 100%;
    .unlock-con{
        width: 0px;
        height: 0px;
        position: absolute;
        left: 50%;
        top: 50%;
        z-index: 11000;
    }
    .layout-text{
        display: inline-block;
        white-space:nowrap;
        position: absolute;
    }
    .main-hide-text .layout-text{
        display: none;
    }
    &-content-container{
        position: relative;
    }
    &-header-con{
        box-sizing: border-box;
        position: fixed;
        display: block;
        width: 100%;
        height: 40px;
        // box-shadow: 0 2px 1px 1px rgba(100,100,100,.1);
        // transition: padding .3s;
    }
    // &-breadcrumb{
    //     padding: 8px 15px 0;
    // }
    &-menu-left{
        background: #464c5b;
        height: 100%;
    }
    .tags-con{
        height: 40px;
        z-index: -1;
        overflow: hidden;
        background: #f0f0f0;
        .tags-outer-scroll-con{
            position: relative;
            box-sizing: border-box;
            padding-right: 120px;
            width: 100%;
            height: 100%;
            .tags-inner-scroll-body{
                position: absolute;
                padding: 2px 10px;
                overflow: visible;
                white-space: nowrap;
                // transition: left .3s ease;
            }
            .close-all-tag-con{
                position: absolute;
                right: 0;
                top: 0;
                box-sizing: border-box;
                padding-top: 8px;
                text-align: center;
                width: 110px;
                height: 100%;
                background: white;
                // box-shadow: -3px 0 15px 3px rgba(0, 0, 0, .1);
                z-index: 10;
            }
        }
    }
    &-header{
        height: 40px;
        background: #fff;
        // box-shadow: 0 2px 1px 1px rgba(100,100,100,.1);
        position: relative;
        z-index: 11;
        // .navicon-con{
        //     margin: 6px;
        //     display: inline-block;
        // }
        // .header-middle-con{
        //     position: absolute;
        //     left: 60px;
        //     top: 0;
        //     right: 340px;
        //     bottom: 0;
        //     padding: 10px;
        //     overflow: hidden;
        // }
        .header-avator-con{
            position: absolute;
            right: 0;
            top: 0;
            height: 100%;
            width: 430px;
            .switch-theme-con{
                display: inline-block;
                width: 40px;
                height: 100%;
            }
            .message-con{
                display: inline-block;
                width: 30px;
                padding: 18px 0;
                text-align: center;
                cursor: pointer;
                i{
                    vertical-align: middle;
                }
            }
            .change-skin{
                font-size: 14px;
                font-weight: 500;
                padding-right: 5px;
            }
            .switch-theme{
                height: 100%;
            }
            .user-dropdown{
                &-menu-con{
                    position: absolute;
                    right: 0;
                    top: 0;
                    width: 150px;
                    height: 100%;
                    .main-user-name{
                        display: inline-block;
                        width: 80px;
                        word-break: keep-all;
                        white-space: nowrap;
                        vertical-align: middle;
                        overflow: hidden;
                        text-overflow: ellipsis;
                        text-align: right;
                    }
                }
                &-innercon{
                    height: 100%;
                    padding-right: 14px;
                }
            }
            .full-screen-btn-con{
                display: inline-block;
                width: 30px;
                padding: 18px 0;
                text-align: center;
                cursor: pointer;
                i{
                    vertical-align: middle;
                }
            }
            .lock-screen-btn-con{
                display: inline-block;
                width: 30px;
                padding: 18px 0;
                text-align: center;
                cursor: pointer;
                i{
                    vertical-align: middle;
                }
            }
        }
    }
    .single-page-con{
        position: absolute;
        top: 41px;
        right: 0;
        bottom: 0;
        overflow: auto;
        background-color: #F0F0F0;
        z-index: 1;
        // transition: left .3s;
        .single-page{
            // margin: 1%;
        }
    }
    &-copy{
        text-align: center;
        padding: 1% 0 20px;
        color: #9ea7b4;
    }
}
.taglist-moving-animation-move{
    // transition: transform .3s;
}
.logo-con{
    padding: 8px;
    text-align: center;
    img{
        height: 44px;
        width: auto;
    }
}
    .logo-con{
        cursor: pointer;
        -webkit-transition:all 0.25s ease-out;transition:all 0.25s ease-out;
        &:hover{
            opacity: 0.7;
        }
    }
    .management{
        position: absolute;
        right: 123px;
        top: 0;
        width: 150px;
        height: 100%;
        line-height: 61px;
    }
    .management .ivu-menu-submenu-title{
        color: #2d8cf0;
    }
    .sidebar-menu-con-ri{
        position:relative;
        width:100vw;
        height:100vh;
        background: #fff;
        .sidebar-menu-con{
            position: absolute;
            top: 0;
            right: 0;
            width:65vw;
            z-index: 21;
            height:100vh;
            overflow: auto;
            // transition: .3s;
            background: rgb(73, 80, 96);
            padding-bottom: 30px;
            .ivu-shrinkable-menu{
                height:auto !important;
            }
            .brs{
                width:100%;
                height:1px;
                background:#a7aab2;
                margin:5px 0;
            }
            .nav_quan{
                width:100% !important;
                margin:0;
            }
        }
        .legr-vlick{
            position: absolute;
            top: 0;
            left: 0;
            width:35vw;
            height:100vh;
            z-index: 20;
            background: rgba(0, 0, 0, 0.6);
            text-align:center;
            line-height:100vh;
            .ivu-icon{
              font-size:2em;
              color: #fff;
            }
        }
        .outline-on{
            color: #fff;
            font-size: 11px;
            font-weight: 100;
            position: fixed;
            right: 0;
            bottom: 0;
        }
    }
    .connavse{
        height:40px;
        .navicon-con-le , .navicon-con , .header-middle-con{
            width: 100%;
            height: 100%;
            text-align: center;
            line-height: 40px;
        }
        .header-middle-con{
           
        }
    }
    /* 可以设置不同的进入和离开动画 */
    /* 设置持续时间和动画函数 */
    .slide-fade-enter-active {
      z-index:10;
      -webkit-transition: all .2s cubic-bezier(1.0, 0.5, 0.8, 1.0);
      transition: all .2s cubic-bezier(1.0, 0.5, 0.8, 1.0);
    }
    .slide-fade-leave-active {
      -webkit-transition: all .2s ease;transition: all .2s ease;
      z-index:10;
    }
    .slide-fade-enter, .slide-fade-leave-to
    /* .slide-fade-leave-active for below version 2.1.8 */ {
      -webkit-transform: translateX(5px);
      transform: translateX(5px);
      opacity: 0;
      z-index:10;
    }
</style>
<template>
    <div class="main">
    <pre style="display: none;">{{currentPath}}</pre>
    <!-- <transition name="slide-fade"> -->
       <div class="sidebar-menu-con-ri" v-if="shrink">
        <div class="sidebar-menu-con">
            <shrinkable-menu 
                @on-change="handleSubmenuChange"
                :theme="menuTheme" 
                :before-push="beforePush"
                :open-names="openedSubmenuArr"
                :menu-list="menuList">
                <div slot="top" class="logo-con" @click="clickHome">
                    <img src="../images/logo.png" key="max-logo" />
                </div>
            </shrinkable-menu>
            <div class="brs"></div>
             <Menu theme="dark" class="nav_quan" @on-select="handleClickUserDropdownse" v-if="auth.user01 || auth.user02">
                <Submenu name="3">
                    <template slot="title">
                        <Icon type="settings"></Icon>
                        系统管理
                    </template>
                    <MenuGroup title="管理">
                         <MenuItem name="0"><Icon type="person-add"></Icon> 用户管理 </MenuItem>
                         <MenuItem name="1"><Icon type="android-wifi"></Icon> IP管理 </MenuItem>
                    </MenuGroup>
                </Submenu>
            </Menu>
              <Button type="text" class="outline-on" @click="loginoutno">
                <Icon type="ios-rewind-outline"></Icon>
                退出登录
             </Button>
         </div>
         <div class="legr-vlick" @click="toggleClick">
             <Icon type="ios-arrow-thin-right"></Icon>
         </div>
        </div>
      <!-- </transition> -->
        <div class="main-header-con" style="padding:0">
            <div class="main-header">
               <Row type="flex" justify="center" class="code-row-bg connavse">
                <Col span="3">
                   <div class="navicon-con-le" v-if="homeye">
                    <Button type="text" @click="backPage">
                        <Icon type="ios-arrow-left" size="32"></Icon>
                    </Button>
                   </div>
                </Col>
                <Col span="18">
                     <div class="header-middle-con">
                        <p>{{timenavtect}}</p>
                    </div>
                </Col>
                <Col span="3">
                   <div class="navicon-con">
                    <Button type="text" @click="toggleClick">
                        <Icon type="ios-more-outline" size="32"></Icon>
                    </Button>
                   </div>
                </Col>
            </Row>
                
               

               <!--  <div class="header-avator-con">
                    <full-screen v-model="isFullScreen" @on-change="fullscreenChange"></full-screen>
                    <lock-screen></lock-screen>

                    <message-tip v-model="mesCount"></message-tip>
                    
                    <theme-switch></theme-switch>

                     <div class="management">
                         <Menu mode="horizontal" @on-select="handleClickUserDropdownse">
                            <Submenu name="3">
                                <template slot="title">
                                    <Icon type="settings"></Icon>
                                    系统管理
                                </template>
                                <MenuGroup title="管理">
                                    <MenuItem name="0"><Icon type="person-add"></Icon> 用户管理 </MenuItem>
                                    <MenuItem name="1"><Icon type="android-wifi"></Icon> IP管理 </MenuItem>
                                </MenuGroup>
                                <MenuGroup title="删除">
                                    <MenuItem name="2"><Icon type="ios-trash-outline"></Icon> 楼盘删除</MenuItem>
                                    <MenuItem name="3"><Icon type="ios-trash"></Icon> 房源删除</MenuItem>
                                </MenuGroup>
                                 <MenuGroup title="记录">
                                    <MenuItem name="4"><Icon type="ios-cog-outline"></Icon> 图片记录</MenuItem>
                                    <MenuItem name="5"><Icon type="ios-cog"></Icon> 跟进记录</MenuItem>
                                </MenuGroup>
                                <MenuGroup title="其他">
                                    <MenuItem name="6"><Icon type="ios-toggle-outline"></Icon> 添加区域/商圈</MenuItem>
                                    <MenuItem name="7"><Icon type="ios-toggle-outline"></Icon> 添加地铁</MenuItem>
                                    <MenuItem name="8"><Icon type="ios-toggle-outline"></Icon> 客户提醒间隔</MenuItem>
                                </MenuGroup>
                            </Submenu>
                        </Menu>
                    </div>

                    <div class="user-dropdown-menu-con">
                        <Row type="flex" justify="end" align="middle" class="user-dropdown-innercon">
                            <Dropdown transfer trigger="click" @on-click="handleClickUserDropdown">
                                <a href="javascript:void(0)">
                                    <span class="main-user-name">{{ userName }}</span>
                                    <Icon type="arrow-down-b"></Icon>
                                </a>
                                <DropdownMenu slot="list">
                                    <DropdownItem name="ownSpace">修改密码</DropdownItem>
                                    <DropdownItem name="loginout" divided>退出登录</DropdownItem>
                                </DropdownMenu>
                            </Dropdown>
                            <Avatar src="http://47.98.155.165/image/vueAdmin/deyu_logo_200x200.jpg" style="background: #619fe7;margin-left: 10px;border:1px solid #eee"></Avatar>
                        </Row>
                    </div>
                </div>
                 -->
            </div>

           <!--  <div class="tags-con">
                <tags-page-opened :pageTagsList="pageTagsList"></tags-page-opened>
            </div> -->
        </div>
        <div class="single-page-con" id="singlepagecon" style="left:0">
            <div class="single-page">
                <keep-alive :include="cachePage">
                    <router-view></router-view>
                </keep-alive>
            </div>
        </div>

         <Modal v-model="editPasswordModal" :closable='false' :mask-closable=false :width="500">
            <h3 slot="header" style="color:#2D8CF0">修改密码</h3>
            <Form ref="editPasswordForm" :model="editPasswordForm" :label-width="100" label-position="right" :rules="passwordValidate">
                <FormItem label="原密码" prop="oldPass" :error="oldPassError">
                    <Input v-model="editPasswordForm.oldPass" placeholder="请输入现在使用的密码" ></Input>
                </FormItem>
                <FormItem label="新密码" prop="newPass">
                    <Input v-model="editPasswordForm.newPass" placeholder="请输入新密码，至少6位字符" ></Input>
                </FormItem>
                <FormItem label="确认新密码" prop="rePass">
                    <Input v-model="editPasswordForm.rePass" placeholder="请再次输入新密码" ></Input>
                </FormItem>
            </Form>
            <div slot="footer">
                <Button type="text" @click="cancelEditPass">取消</Button>
                <Button type="primary" :loading="savePassLoading" @click="saveEditPass">保存</Button>
            </div>
        </Modal>
         <Modal v-model="timese" :closable='false' :mask-closable='false'>
            <h3 slot="header">警告</h3>
            <p>下班时间无法使用</p>
            <div slot="footer">
               
            </div>
        </Modal>

    </div>
</template>
<script>
    import shrinkableMenu from './main-components/shrinkable-menu/shrinkable-menu.vue';
    import tagsPageOpened from './main-components/tags-page-opened.vue';
    import breadcrumbNav from './main-components/breadcrumb-nav.vue';
    import fullScreen from './main-components/fullscreen.vue';
    import lockScreen from './main-components/lockscreen/lockscreen.vue';
    import messageTip from './main-components/message-tip.vue';
    import themeSwitch from './main-components/theme-switch/theme-switch.vue';
    import Cookies from 'js-cookie';
    import util from '@/libs/util.js';
    import axios from 'axios'
    import localStorages from '../localStorage/localStorage';
    export default {
        components: {
            shrinkableMenu,
            tagsPageOpened,
            breadcrumbNav,
            fullScreen,
            lockScreen,
            messageTip,
            themeSwitch
        },
        data () {
            const valideRePassword = (rule, value, callback) => {
                if (value !== this.editPasswordForm.newPass) {
                    callback(new Error('两次输入密码不一致'));
                } else {
                    callback();
                }
            };
            return {
                shrink: false,
                homeye: false,
                editPasswordModal: false, // 修改密码模态框显示
                savePassLoading: false,
                timese: false,
                oldPassError: '',
                timenavtect:'首页',
                editPasswordForm: {
                oldPass: '',
                newPass: '',
                rePass: ''
                },
                passwordValidate: {
                    oldPass: [
                        { required: true, message: '请输入原密码', trigger: 'blur' }
                    ],
                    newPass: [
                        { required: true, message: '请输入新密码', trigger: 'blur' },
                        { min: 6, message: '请至少输入6个字符', trigger: 'blur' },
                        { max: 32, message: '最多输入32个字符', trigger: 'blur' }
                    ],
                    rePass: [
                        { required: true, message: '请再次输入新密码', trigger: 'blur' },
                        { validator: valideRePassword, trigger: 'blur' }
                    ]
                },
                userName: '',
                forms: [],
                auth:{},
                keya:Cookies.set('keya'),
                isFullScreen: false,
                // openedSubmenuArr: ['recomm_end','overview','building','house','client']
                openedSubmenuArr: this.$store.state.app.openedSubmenuArr //默认侧边打开
            };
        },
        computed: {
            menuList () {
                return this.$store.state.app.menuList;
            },
            pageTagsList () {

                return this.$store.state.app.pageOpenedList; // 打开的页面的页面对象
            },
            currentPath () {
                let a = this.$store.state.app.currentPath
                // console.log(a[a.length - 1])
                // homeye
                this.timenavtect = a[a.length - 1].title
                if (this.timenavtect =="工作概览" || this.timenavtect =="首页") {
                    this.homeye = false
                }else{
                    this.homeye = true
                }
                return this.$store.state.app.currentPath; // 当前面包屑数组
            },
            avatorPath () {
                return localStorage.avatorImgPath;
            },
            cachePage () {
                return this.$store.state.app.cachePage;
            },
            lang () {
                return this.$store.state.app.lang;
            },
            menuTheme () {
                return this.$store.state.app.menuTheme;
            },
            mesCount () {
                return this.$store.state.app.messageCount;
            }
        },
        methods: {
            accesse(){
             let _this = this;
             axios({
                method: 'post',
                url: '/api/power',
                headers: { Authorization: 'Bearer ' + Cookies.set('keya') },
              })
              .then(function(res) {
                   Cookies.set('auth', res.data.power); //权限
                  _this.auth = res.data.power;
              })
              .catch(function(err) {
                  _this.$Notice.error({ title: '权限获取错误' });
              })
          },
            init () {
                let pathArr = util.setCurrentPath(this, this.$route.name);
                this.$store.commit('updateMenulist');
                if (pathArr.length >= 2) {
                    this.$store.commit('addOpenSubmenu', pathArr[1].name);
                }
                this.userName = Cookies.get('user');
                let messageCount = 3;
                this.messageCount = messageCount.toString();
                this.checkTag(this.$route.name);
                this.$store.commit('setMessageCount', 4);
            },
            toggleClick () {
                this.shrink = !this.shrink;
            },
            backPage () {
                this.$router.go(-1);
            },
            cancelEditPass () {
              this.editPasswordModal = false;
            },
            saveEditPass () {
                this.$refs['editPasswordForm'].validate((valid) => {
                    if (valid) {
                        this.savePassLoading = true;
                        // you can write ajax request here
                    }
                });
            },
            handleClickUserDropdown (name) {
                if (name === 'ownSpace') {
                    // util.openNewPage(this, 'ownspace_index');
                    // this.$router.push({
                    //     name: 'ownspace_index'
                    // });
                      this.editPasswordModal = true;
                } else if (name === 'loginout') {
                    this.$store.commit('logout', this);
                    this.$store.commit('clearOpenedSubmenu');
                    this.$router.push({
                        name: 'login'
                    });
                }
            },
            loginoutno(){
                 this.$store.commit('logout', this);
                    this.$store.commit('clearOpenedSubmenu');
                    this.$router.push({
                        name: 'login'
                    });
            },
            checkTag (name) {
                let openpageHasTag = this.pageTagsList.some(item => {
                    if (item.name === name) {
                        return true;
                    }
                });
                if (!openpageHasTag) { // 解决关闭当前标签后再点击回退按钮会退到当前页时没有标签的问题
                    util.openNewPage(this, name, this.$route.params || {}, this.$route.query || {});
                }
            },
            handleSubmenuChange (val) {
                // console.log(val)
            },
            beforePush (name) {
                // if (name === 'accesstest_index') {
                //     return false;
                // } else {
                //     return true;
                // }
                return true;
            },
            fullscreenChange (isFullScreen) {
                // console.log(isFullScreen);
            },
            clickHome(){
                //点击回到首页
               this.$router.push({
                 name: 'home_index'
                });
            },
            cuno(){
               this.$router.push({
                 name: 'error-403'
                });
            },
            handleClickUserDropdownse(e){
                if (e==0) {
                    if (this.auth.user01 || auth.user02) {
                         this.$router.push({
                          name: 'user_admin'
                         })
                    }else{
                        this.cuno();
                    }


                }else if(e == 1){

                    if (this.auth.syst01) {
                        this.$router.push({
                        name: 'add_ip'
                       }) 
                    }else{
                       this.cuno(); 
                    }
                    

                }else if(e == 2){

                   if (this.auth.syst04) {
                    this.$router.push({
                      name: 'lou_reover'
                    })
                    }else{
                      this.cuno(); 
                    }
                    

                }else if(e == 3){
                    // syst03
                      if (this.auth.syst03){
                           this.$router.push({
                              name: 'fang_reover'
                            })
                      }else{
                       this.cuno(); 
                      }
                   

                }else if(e == 4){
                    // syst02
                    if (this.auth.syst02) {
                          this.$router.push({
                          name: 'recording_img'
                        })
                    }else{
                       this.cuno();  
                    }
                   
                }else if(e == 6){
                    this.$router.push({
                      name: 'dist_rict'
                    })
                }else if(e == 7){
                    this.$router.push({
                      name: 'add_metro'
                    })
                }else if(e == 5){
                    if (this.auth.syst08) {
                        this.$router.push({
                         name: 'follow_up'
                       })
                    }else{
                      this.cuno();    
                    }
                    
                }else if(e == 8){
                    this.$router.push({
                      name: 'alterna_tion'
                    })
                }
            }
        },
        watch: {
            '$route' (to) {
                this.shrink = false;
                this.$store.commit('setCurrentPageName', to.name);
                let pathArr = util.setCurrentPath(this, to.name);
                if (pathArr.length > 2) {
                    this.$store.commit('addOpenSubmenu', pathArr[1].name);
                }
                this.checkTag(to.name);
                localStorage.currentPageName = to.name;
                // this.timenavtect
            },
            lang () {
                util.setCurrentPath(this, this.$route.name); // 在切换语言时用于刷新面包屑
            }
        },
        mounted () {
            this.init();
            this.accesse();
            console.log(22)
            this.forms = localStorages.getStorage('forms');
            // let tineData = new Date();
            // if (tineData.getHours() >= 19) {
            //     this.timese = true
            // }
        },
        created () {
            // 显示打开的页面的列表
            this.$store.commit('setOpenedList');

        }
    };
</script>
