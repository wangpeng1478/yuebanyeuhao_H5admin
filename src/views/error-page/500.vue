<style lang="less">
   .error500{
     width:100vw;
     height:100vh;
     position:relative;
     .error500-body-con{
        position:absolute;
        top:0;
        left:0;
        right:0;
        bottom:0;
        margin:auto;
        width:90vw;
        height:90vw;
        text-align:center;
        .error500-body-con-title{
            color: #F44336;
            font-size:2em;
            font-weight:800;
        }
        .error500-btn-con{
            margin:10vw 0 5vw 0
        }
     }
   }
</style>

<template>
    <div class="error500">
        <div class="error500-body-con">
            <Card>
                <div class="error500-body-con-title">
                    500
                </div>
                <p class="error500-body-con-message">服务器内部错误</p>
                <div class="error500-btn-con">
                <Row>
                    <Col span="12"><Button @click="goHome" type="text" long>返回首页</Button></Col>
                    <Col span="12"><Button @click="backPage" type="error" long>返回上一页</Button></Col>
                </Row>
                </div>
            </Card>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Error500',
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
