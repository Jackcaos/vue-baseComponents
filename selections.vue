<template>
    <div class="selection-component">
      <div class="selection-show" @click="toggleDrop">
        <span>{{ selections[nowIndex].label }}</span>
        <div class="arrow"></div>
      </div>
      <div class="selection-list" v-if="isDrop">
        <ul>
          <li v-for="(item, index) in selections" :key="item.id" @click="chooseSelection(index)">
              {{ item.label }}</li>
        </ul>
      </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      isDrop: false,
      nowIndex: 0,
       selections: [
        {
          label: '1',
          value: 0
        },
        {
          label: '大二',
          value: 1
        },
        {
          label: '大三',
          value: 2
        }
      ]
    }
  },
  methods: {
    toggleDrop () {
      this.isDrop = !this.isDrop
    },
    chooseSelection (index) {
      this.nowIndex = index
      this.isDrop = false
    //   this.$emit('on-change', this.selections[this.nowIndex])
    }
  }
}
</script>

<style scoped>
.selection-component {
    /* 设置好总的布局模式inline-block */
      /* position: relative;
      left:100px; */
      display: inline-block;
    }
    .selection-show {
      /* 设置好整个框的样子，height */
      border: 1px solid #e3e3e3;
      padding: 0 20px 0 10px;
      display: inline-block;
      cursor: pointer;
      height: 25px;
      line-height: 25px;
      border-radius: 3px;
      background: #fff;
    }

    .selection-show .arrow {
     /* 设置箭头的样式 */
      display: inline-block;
      border-left: 4px solid transparent;
      border-right: 4px solid transparent;
      border-top: 5px solid #e3e3e3;
      width: 0;
      height: 0;
      margin-top: -1px;
      margin-left: 30px;
      margin-right: -14px;
      vertical-align: middle;
    }
    .selection-list {
        /* 将下拉列表绝对定位加在输入框下面 */
      display: inline-block;
      position: absolute;
      left: 0;
      top: 25px;
      width: 100%;
      background: #fff;
      border-top: 1px solid #e3e3e3;
      border-bottom: 1px solid #e3e3e3;
      z-index: 5;
    }
    .selection-list ul {
        /* 去掉ul的padding和margin */
     padding: 0px;
     margin:0px;
    }
    .selection-list li {
        /* 设置相关选项的布局，边界，过多的文字进行隐藏 */
      padding: 5px 5px 5px 10px;
      float: left;
      border-left: 1px solid #e3e3e3;
      border-right: 1px solid #e3e3e3;
      cursor: pointer;
      background: #fff;
      list-style-type: none;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      width:86%;
    }
    .selection-list li:hover {
      background: #e3e3e3;
    }
</style>
