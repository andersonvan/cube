<template>
  <div class="container">
    <div id="cube">
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <div>4</div>
      <div>5</div>
      <div>6</div>
      <div class="fillter"></div>
      <div class="fillter"></div>
      <div class="fillter"></div>
      <div class="fillter"></div>
      <div class="fillter"></div>
      <div class="fillter"></div>
      <div class="fillter"></div>
      <div class="fillter"></div>
      <div class="fillter"></div>
    </div>
    <div id="test"></div>
    <cube :setHight="hight"/>
  </div>
</template>
<script>
import Cube from './Cube'
export default {
  name: '',
  components: {Cube},
  props: {},
  data () {
    return {
      hight:'500px'
    }
  },
  computed: {},
  watch: {},
  created () {},
  mounted () {
    var oDiv = document.querySelector('#cube');
    var x = 30;
    var y = -60;
    oDiv.onmousedown = function(ev){
       var event = window.event || ev;
       var disY = event.clientX - y;
       var disX = event.clientY - x;
       document.onmousemove = function(ev){
           var event = window.event || ev;
           // 计算偏移角度
           x = event.clientY - disX;
           y = event.clientX - disY;
           oDiv.style.transform = 'perspective(800px) rotateY('+y+'deg) rotateX('+x+'deg)'
       }
       document.onmouseup = function(){
           document.onmousemove = null;
       }
       return false;
   }
  },
  methods: {}
}
</script>
<style scoped lang="less">
#cube {
  position:relative;
  top:300px;
  left:0;
  width: 200px;
  height:200px;
  // margin: 300px auto;
  // border:1px solid #333;
  margin:0px auto;
  transform-style: preserve-3d;
  transform: rotate3d(1, 1, 0, -45deg);
}
#cube > div {
  // width: 50px;
  // height: 50px;
  height: 100%;
  width: 100%;
  border: 1px solid #eee;
  position: absolute;
  top: 0;
  left: 0;
  text-align: center;
  line-height: 200px;
  clip-path: polygon(25% 0%, 75% 0%, 100% 25%, 100% 75%, 75% 100%, 25% 100%, 0% 75%, 0% 25%)
}
#cube > div:nth-child(1){
  transform:translateZ(100px);
  background-color: red;
}
#cube > div:nth-child(2){
  transform:translateZ(-100px);
  background-color: rgb(0, 38, 255);
}
#cube > div:nth-child(3){
  transform:rotateY(90deg) translateZ(100px);
  background-color: rgb(0, 255, 0);
}
#cube > div:nth-child(4){
  transform:rotateY(-90deg) translateZ(100px);
  background-color: rgb(251, 255, 0);
}
#cube > div:nth-child(5){
  transform:rotateX(90deg) translateZ(100px);
  background-color: rgb(253, 253, 253);
}
#cube > div:nth-child(6){
  transform:rotateX(-90deg) translateZ(100px);
  background-color: rgb(0, 0, 0);
}

#cube > div.fillter{
  background-color: orange;
  clip-path: polygon(50% 0, 50% 50%,0% 50%)
}
#test {
  position: absolute;
  top: 100px;
  left: 300px;
  height: 200px;
  width: 200px;
  background-color: lightgreen;
  clip-path: polygon(22% 0, 44% 22%,0% 22%)

}

</style>
