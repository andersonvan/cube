<template>
  <div>
    <div class="my-triangle">2</div>
    <div class="my-triangle">2</div>
    <div class="my-triangle">2</div>
    <div class="my-triangle">2</div>
    <div class="my-triangle">2</div>
    <div class="my-triangle">2</div>
    <div class="my-triangle">2</div>
    <div class="my-triangle">2</div>
    <div class="my-triangle">2</div>
    <div id="tt"></div>
  </div>
</template>
<script>
export default {
  name: 'Cube',
  components: {},
  props: {
    setHight: {
      type: String,
      required: true
    }
  },
  data () {
    return {}
  },
  computed: {},
  watch: {},
  created () {},
  mounted () {},
  methods: {
//     triangle(@height){
//   @h: @height;
//   @w: tan(30deg) * 2 * @h;
//   width: @w;
//   height: @h;
//   clip-path: polygon(@w/2 0, @w @h, 0 @h);
// }
  }
}

</script>
<style scoped lang="less">
@height: 100px;
.equ-triangle{
  @h: @height;
  // @w: tan(30deg) * 2 * @h;
  @w: tan(30deg) * 2 * @h;
  width: @w;
  height: @h;
  clip-path: polygon(@w/2 0, @w @h, 0 @h);
}
.my-triangle {
  .equ-triangle;
  background: #f00;
}
#tt {
  width: 100px;
  height: 100px;
  background-color: black;
}
</style>
