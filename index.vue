<template>
    <div>
        <van-cell-group>
        <van-field   v-model="phone"
                label="手机号q"
                placeholder="请输入手机号"
                :error-message="mes"> 
        </van-field>
        <van-field   v-model="phone1"
                label="手机号33333"
                placeholder="请输入手机号"
                :error-message="mes"> 
        </van-field>
        </van-cell-group>
        <div @click='goTest1'>店家</div>
        <div class="box" style="width: 100%; height: 1000px; border: solid 1px red; box-sizing: border-box;"></div>

        <div class="box1" id="port" style="width: 100%; height: 600px; border: solid 1px blue; margin-top: 10px;"></div>
    </div>
</template>


<script>

import { Field, CellGroup, Button  } from 'vant';
export default {
    name: 'mohu',
    components: {
       [Field .name]: Field ,
       [Button .name]: Button ,
       [CellGroup .name]: CellGroup ,
    },
    data() {
       return {
           phone: '',
           mes: '手机号格式错误',
           phone1: ''
       }
    },
    created() {
        // 创建时执行跳转锚点位置
        this.$nextTick(() => {this.getloacl()})
        
    },
    activated() {
        this.phone = this.$route.query.ids
        window.console.log('test',this.$route.query.ids);
    },
    mouted() {
        this.$nextTick(function() {
            window.addEventListener('scroll',this.handleScroll)
        })
    },

    methods: {
        goTest1() {
            this.$router.push({
                name: 'cart',
                query:{
                    ids: this.msg
                }
            })
        },
        getloacl() {
        
            let select = this.$route.params.id
            let elm = document.getElementById(select);
            if(select) {
                elm.scrollIntoView(true)
            }
        },
        // 离开页面时对loaclStorage中的id进行销毁，避免其它入口进来有锚点问题
        destroyed() {
            localStorage.setItem('id','')
        },
  }

    
}
</script>