<template>
    <div class="chooser-component">
        <div>
        <ul class="chooser-list">
          <li
          v-for="(item, index) in selections"
          @click="chosenSelection(index)"
          :title="item.label"
          :class="{active:index === nowIndex}" :key="item.id"
          >{{ item.label }}</li>
        </ul>
      </div>
    </div>
</template>

<script>
export default {
    props:{
        selections:{
            type:Array,
            default:{
                label:'大一',
                value:0
            }
        }
    },
  data(){
    return {
 
      nowIndex: 0
    }
  },
  methods: {
    chosenSelection (index) {
      this.nowIndex = index
    //   this.$emit('on-change', this.selections[index])
    }
  }
}
</script>

<style scoped>
.chooser-component {  
    /* 记住整体的布局应该使用inline-block */
  position: relative;
  display: inline-block;
}
.chooser-list li{
    /* 在li中添加choose的布局格式，边距大小，字体的显示格式的padding，及鼠标的样式 */
  display: inline-block;
  border: 1px solid #e3e3e3;
  height: 25px;
  line-height: 25px;
  padding: 0 8px;
  /* margin-top:5px; */
  margin-right: 5px;
  border-radius: 3px;
  text-align: center;
  cursor: pointer;
}
.chooser-list li.active {
    /* 展示点击完后的样式 */
  border-color: #4fc08d;
  background: #4fc08d;
  color: #fff;
}
</style>
