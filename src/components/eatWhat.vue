<template>
  <div class="eat-container" :style="Height">
    <header class="eat-header">康康吃什么</header>
    <section class="eat-body">
      <p style="height: 100px">{{ foodName }}</p>
      <div v-if="current == 0" class="eat-btn" @click="hanldEating">
        开始随缘
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 容器高度
      Height: undefined,
      foodName: undefined,
      isWhile: false,
      current: 0,
      // 菜谱
      foodMenu: ["热干面", "臊子面", "麻辣烫", "千层饼"],
    };
  },
  created() {
    this.Height = {
      height: window.innerHeight + "px",
    };
  },
  methods: {
    async hanldEating() {
      let idx = this.current;
      let timer = null
      this.isWhile = !this.isWhile;
      console.log("开始循环", this.isWhile);
      
        clearInterval(timer);
    
      if(timer == null ) {
          
        timer = setInterval(() => {
            this.foodName = this.foodMenu[idx];
            if (idx < this.foodMenu.length) {
                idx++;
                } else {
                idx = 0;
                }
        }, 100);
        
      }


      
    },
  },
};
</script>

<style lang="scss">
.eat-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
  .eat-header {
    text-align: center;
    font-size: 18px;
    font-weight: bold;
    letter-spacing: 2px;
  }
  .eat-body {
    .eat-btn {
      width: 100px;
      line-height: 40px;
      text-align: center;
      font-size: 12px;
      border: 1px solid #888;
      cursor: pointer;
    }
  }
}
</style>