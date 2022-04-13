<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="big-circle">
      <LuckyWheel
        ref="myLucky"
        width="300px"
        height="300px"
        :prizes="prizes"
        :blocks="blocks"
        :buttons="buttons"
        @start="startCallback"
        @end="endCallback"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      blocks: [
        {
          padding: "13px",
          // background: "#617df2",
          imgs: [
            {
              src: "https://cdn.jsdelivr.net/gh/buuing/cdn/demo/wheel-border.jpg",
              width: "100%",
              height: "100%",
            },
          ],
        },
        {
          padding: "10px",
          imgs: [
            {
              src: "https://cdn.jsdelivr.net/gh/buuing/cdn/demo/wheel-border.png",
              width: "100%",
              height: "100%",
            },
          ],
        },
        {
          padding: "20px",
          imgs: [
            {
              src: "https://cdn.jsdelivr.net/gh/buuing/cdn/demo/block-img.png",
              width: "100%",
              rotate: true,
            },
          ],
        },
      ],
      prizes: [
        { fonts: [{ text: "", top: "10%" }],},
        { fonts: [{ text: "", top: "10%" }],},
        { fonts: [{ text: "", top: "10%" }],},
        { fonts: [{ text: "", top: "10%" }],},
        { fonts: [{ text: "", top: "10%" }], },
        { fonts: [{ text: "", top: "10%" }], },
      ],
      buttons: [
        { radius: "50px", background: "#617df2" },
        { radius: "45px", background: "#afc8ff" },
        {
          radius: "40px",
          background: "#869cfa",
          // pointer: true,
          fonts: [{ text: "开始\n抽奖", top: "-20px" }],
        },
      ],
    };
  },
  methods: {
    // 点击抽奖按钮会触发star回调
    startCallback() {
      // 调用抽奖组件的play方法开始游戏
      this.$refs.myLucky.play();
      // 模拟调用接口异步抽奖
      setTimeout(() => {
        // 假设后端返回的中奖索引是0
        const index = 0;
        // 调用stop停止旋转并传递中奖索引
        this.$refs.myLucky.stop(index);
      }, 3000);
    },
    // 抽奖结束会触发end回调
    endCallback(prize) {
      console.log(prize);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.big-circle {
  position: absolute;
  top: 200px;
  left: 200px;
  width: 300px;
  height: 300px;
}
</style>
