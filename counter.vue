<template>
    <div class="counter-component">
      <div class="counter-btn" @click="minus"> - </div>
      <div class="counter-show">
        <input type="text" v-model="number" @keyup="fixNumber">
      </div>
      <div class="counter-btn" @click="add"> + </div>
    </div>
</template>

<script>
export default {
  props: {
    max: {
      type: Number,
      default: 5
    },
    min: {
      type: Number,
      default: 1
    }
  },
  data () {
    return {
      number: this.min
    }
  },
  watch: {
    number () {
    //   this.$emit('on-change', this.number)
    }
  },
  methods: {
    fixNumber () {
      let fix
      if (typeof this.number === 'string') {
        fix = Number(this.number.replace(/\D/g, ''))
      }
      else {
        fix = this.number
      }
      if (fix > this.max || fix < this.min) {
        fix = this.min
      }
      this.number = fix
    },
    minus () {
      if (this.number <= this.min) {
        return
      }
      this.number --
    },
    add () {
      if (this.number >= this.max) {
        return
      }
      this.number ++
    }
  }
}
</script>

<style scoped>
.counter-component {
    /* 首先定义position,然后为了避免块级换行问题将display设为inline-block,为之后的数字也设置上隐藏和居中样式 */
  position: relative;
  display: inline-block;
  overflow: hidden;
  vertical-align: middle;
}
.counter-show {
    /* 将3个div进行左浮动 */
  float: left;
}
.counter-show input {
    /* 设置输入框中的样式,高宽以及边界 */
  border: none;
  border-top: 1px solid #e3e3e3;
  border-bottom: 1px solid #e3e3e3;
  height: 23px;
  line-height: 23px;
  width: 30px;
  outline: none;
  text-indent: 4px;
}
.counter-btn {
    /* 给两个点击的按钮设置样式 */
  border: 1px solid #e3e3e3;
  float: left;
  height: 25px;
  line-height: 25px;
  width: 25px;
  text-align: center;
  cursor: pointer;
}
.counter-btn:hover {
    /* 设置鼠标的hover效果 */
  border-color: #4fc08d;
  background: #4fc08d;
  color: #fff;
}

</style>
