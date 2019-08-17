<template>
	<view @click="a()" :animation="animationData" style="background:red;height:100upx;width:100upx"></view>
</template>
<script>
	export default{
  data: {
    animationData: {}
  },
  onShow: function(){
    var animation = uni.createAnimation({
      duration: 1000,
        timingFunction: 'ease',
    })

    this.animation = animation

    animation.scale(2,2).rotate(45).step()

    this.animationData = animation.export()

    setTimeout(function() {
      animation.translate(30).step()
      this.animationData = animation.export()
    }.bind(this), 1000)
  },
  methods:{
   a() {
	   this.animation.translate(100, 100).step({ duration: 1000 })
   }
  }
}
</script>