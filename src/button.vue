<template>
    <button class="g-button" :class="{[`icon-${iconPosition}`]:true}"
    @click="x">
         <!-- <button calss="g-button" :class="{'undefined':true}">
         <button calss="g-button" :class="{'right':true}">
         <button calss="g-button" :class="{'left':true}"> -->
       <g-icon  class="icon" v-if="icon && !loading" :name="icon"></g-icon>
       <g-icon class="loading icon" v-if="loading" name="loading"></g-icon>
        <div class="content">
        <slot></slot>
      </div>
    </button>
</template>
<script>
import Icon from './icon'
//`#i-${icon}`模板字符串插值。插入一个icon .icon的值是从props获得的，
            //props的值是通过index.html icon="settings"传过来的
            //实现用户在index,html输入settings我们就给了icon
export default {
    components:{
        'g-icon':Icon
    },
    // props:['icon','iconPosition']//icon位置 left right
    props:{
        icon: {},
        loading:{
            type:Boolean,
            default:false
        },
        iconPosition: {
            typen: String,
            default: 'left',
            validator (value){
                console.log(value)
                if(value!=='left' && value!=='right'){
                    return false
                }else{
                    return true;}
            }
        }
    },
    methods:{
        x(){
            this.$emit('click')
        }
    }
}
</script>
<style lang="scss">
@keyframes spin{
    0%{ transform: rotate(0deg);}
    100%{ transform: rotate(360deg);}
}
  .g-button{
            font-size: var(--font-size);
            height:var(--button-height);
            padding: 0 1em;
            border-radius: var(--border-radius);
            border: 1px solid var(--border-color);
            background: var(--button-bg);
            display: inline-flex;
            justify-content: center;
            align-items: center; 
            vertical-align: middle;        
        &:hover{
            border-color:var(--border-color-hover);
        }//&表示当前选择器
        &:active{
            background-color: var(--button-active-bg);
        }
        &:focus{
            outline: none;
        }
        > .content{
            order:2;
        }
        >.icon{
            order:1;
            margin-right: .1em;;
        }
        &.icon-right{
            >.content{
                order:1;
            }
            >.icon{
                order:2;
                margin-right: 0;
                margin-left: .1em;
            }
        }
        .loading{
            animation: spin 1s  infinite linear;//滚2s 无线的滚，线性的滚

        }
  }

</style>