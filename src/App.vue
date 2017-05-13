<template>
    <header>
        <a class="eui-icon eui-icon-{{header.lefticon}} eui-position-left"></a>
        <h1 class="eui-title">{{header.title}}</h1>
        <a class="eui-icon eui-icon-{{header.righticon}} eui-position-right"></a>
    </header>
    <div class="eui-wrap-page">
        <div class="eui-scroller">
            <component :is="view"></component>
            <template id="home">
                <div>我是首页</div>
            </template>
            <template id="find">
                <div>我是发现</div>
            </template>
            <template id="message">
                <ve-messagelist :listdata="message.listdata"></ve-messagelist>
            </template>
            <template id="person">
                <div>我是个人</div>
            </template>
        </div>
    </div>
    <footer class="eui-footer">
        <ul class="eui-bottom-bar">
            <li v-for="item in footer" v-on:click="tabbar($index)" v-bind:class="{'eui-tab-current':initIndex===$index}"> <i class="eui-icon eui-icon-{{item.icon}}"></i> <span>{{item.title}}</span> </li>
        </ul>
    </footer> 
</template>

<script>
    export default {
         config: {
                el: "#app"
                , initIndex: 1, //[初始化参数,默认为第一个]
                tplID: ['home', 'find', 'message', 'person']
                , header: [
                    {
                        lefticon: 'bars'
                        , title: '首页'
                        , righticon: 'about'
                    }
                    , {
                        lefticon: 'position'
                        , title: '发现'
                        , righticon: 'add'
                    }
                    , {
                        title: '消息'
                        , righticon: 'personadd'
                    }
                    , {
                        title: '个人'
                        , righticon: 'personadd'
                    }
				]
                , footer: [
                    {
                        icon: 'home'
                        , title: '首页'
                    }
                    , {
                        icon: 'find'
                        , title: '发现'
                    }
                    , {
                        icon: 'message'
                        , title: '消息'
                    }
                    , {
                        icon: 'person'
                        , title: '个人'
                    }
				]
            }
            , data: {
                home: {}
                , message: {
                    listdata: [
                        {
                            path: ''
                            , logo: 'img/eui-chat-1.png'
                            , name: '智能小助手1'
                            , time: '12:00'
                            , msg: '我是萌萌哒的机器人'
                            , msgnum: '1'
                        }
                        , {
                            path: ''
                            , logo: 'img/eui-chat-2.png'
                            , name: '智能小助手2'
                            , time: '12:00'
                            , msg: '我是萌萌哒的机器人,你说什么鬼？哈哈哈'
                            , msgnum: '99+'
                        }
			    	]
                }
            },
        components: {
        }
    }
</script>

<style>
    


/*底部*/

footer{
    width: 100%;
    height: .95rem;
    border-top: 1px solid #EBEBEB;
    display: -webkit-box;
    background: white;
    dl {
        -webkit-box-flex: 1;
        text-align: center;
        position: relative;
        dt {
            width: .42rem;
            height: .42rem;
            position: absolute;
            top: .13rem;
            left: 50%;
            margin-left: -.21rem;
        }
        dd {
            width: 100%;
            height: .30rem;
            font-size: .2rem;
            color: #808080;
            position: absolute;
            top: .6rem;
        }
        &:nth-of-type(1) {
            dt {
                background: url("../img/home1@3x.png") no-repeat;
                background-size: 100%;
            }
            dd {
                color: #44b7f7;
            }
        }
        &:nth-of-type(2) {
            dt {
                background: url("../img/supermarket@3x.png") no-repeat;
                background-size: 100%;
            }
        }
        &:nth-of-type(3) {
            dt {
                background: url("../img/intelligence@3x.png") no-repeat;
                background-size: 100%;
            }
        }
        &:nth-of-type(4) {
            dt {
                background: url("../img/my1@3x.png") no-repeat;
                background-size: 100%;
            }
        }
    }
}
</style>