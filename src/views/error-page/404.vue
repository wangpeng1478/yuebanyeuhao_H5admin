<style lang="less">
    .error404{
     width:100vw;
     height:100vh;
     position:relative;
     .error404-body-con{
        position:absolute;
        top:0;
        left:0;
        right:0;
        bottom:0;
        margin:auto;
        width:90vw;
        height:90vw;
        text-align:center;
        .error404-body-con-title{
            color: #2d8cf0;
            font-size:2em;
            font-weight:800;
        }
        .error404-btn-con{
            margin:10vw 0 5vw 0
        }
     }
   }
</style>

<template>
    <div class="error404">
        <div class="error404-body-con">
            <Card>
                <div class="error404-body-con-title">
                    404
                </div>
                <p class="error404-body-con-message">
                    没有找到页面
                </p>
                <div class="error404-btn-con">
                     <Row>
                    <Col span="12"><Button @click="goHome" type="text" long>返回首页</Button></Col>
                    <Col span="12"><Button @click="backPage" type="primary" long>返回上一页</Button></Col>
                </Row>
                </div>
            </Card>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Error404',
    methods: {
        backPage () {
            this.$router.go(-1);
        },
        goHome () {
            this.$router.push({
                name: 'home_index'
            });
        }
    }
};
</script>
