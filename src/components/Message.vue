<template>
  <div v-show="show" :class="`alert alert-${type} alert-dismissible`">
    <button @click="close" type="button" class="close"><span>×</span></button>
    {{ msg }}
  </div>
</template>

<script>
export default {
  name:"Message",
  props:{
    show:{
      type:Boolean,
      default:false
    },
    type:{
      type:String,
      default:'success'
    },
    msg:{
      type:String,
      default:''
    }
  },
    watch: {
    show(value) {
      if (value) {
        this.$nextTick(() => {
          this.$el.scrollIntoView(true)
        })
      }
    }
  },
  methods: {
    close() {
      this.$emit('update:show', false)
      // 不可以直接修改 show，这会导致 Vue 在控制台发出错误警告
      this.show = false
    }
  }
}
</script>

<style scoped>

</style>