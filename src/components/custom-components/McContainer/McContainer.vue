<template>
  <div class="cnt">
    <div class="cnt-header" :style="{backgroundColor:headBgc,color:titleColor}">
      {{title}}
    </div>
    <div class="container" :style="{paddingBottom:padding+'px',paddingTop:padding+'px'}">
      <div :style="getCoreContentStyle">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import {computed} from "vue";

const props=withDefaults(defineProps<{
  padding:number,
  title:string,
  headBgc:string,
  minHeight:number,
  contentBgc:string,
  titleColor:string,
}>(),{
  padding:0,
  title:"容器标头",
  headBgc:"#DD6161",
  minHeight:50,
  titleColor:"#000",
  contentBgc:"#e6e6e6",
});
const getCoreContentStyle=computed(()=>{
  return {
    minHeight: props.minHeight+'px',
    backgroundColor: props.contentBgc,
  }
});
// export default {
//   name: "McContainer",
//   props:{
//     padding:{
//       type:Number,
//       default:0
//     },
//     title:{
//       type:String,
//       default:"容器标头",
//     },
//     headBgc:{
//       type:String,
//       default:"#DD6161",
//     },
//     minHeight:{
//       type:Number,
//       default:50
//     },
//     contentBgc:{
//       type:String,
//       default:"#e6e6e6",
//     }
//   },
//   computed:{
//     getCoreContentStyle(){
//       return {
//         minHeight: this.minHeight+'px',
//         backgroundColor: this.contentBgc,
//       }
//     }
//   }
// };
</script>

<style lang="scss" scoped>
.cnt{
  .cnt-header{
    text-align: center;
    line-height: 30px;
    height:30px;
  }
  .container{
    border: 1px solid #13ce66;
  }
}
</style>