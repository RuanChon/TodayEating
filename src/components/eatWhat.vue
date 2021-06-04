<template>
  <div class="eat-container" :style="Height">
    <header class="eat-header">康康吃什么</header>
    <section class="eat-body">
      <p class="eat-name">{{ foodName }}</p>
      <div v-if="!isWhile" class="eat-btn" @click="hanldEating">开始随缘</div>
      <div v-else class="eat-btn" @click="hanldStop">就是它了！</div>
    </section>

    <footer class="eat-footer">
        <p>Author：RuanChon -- 2021/06/03</p>
    </footer>
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
      // 菜谱
      foodMenu: [
          "热干面", 
          "臊子面", 
          "麻辣烫", 
          "千层饼", 
          "螺蛳粉", 
          "火锅", 
          "鸡公煲", 
          "盖饭", 
          "披萨", 
          "炸鸡汉堡", 
          "烧烤炸炸", 
          "小龙虾", 
          "养生粥",
          "馄饨",
          "包子",
          "烤肉",
          "冒菜",
          "麻辣香锅",
          "煎饼果子",
          "锅盔",
          "沙拉",
          "炒牛河",
          "咖喱饭",
          "蛋糕面包",
          "牛排",
          "酸菜鱼",
          "关东煮",
          "车仔面",
          "臭豆腐",
          "椰子鸡",
          "寿司",
          "肠粉",
          "豆皮",
          "拌饭",
          "饺子",
          "周黑鸭",
          "新疆菜",
          "川菜",
          "东北菜",
          "粤菜",
          "东南亚菜",
          "云南米线",
          "南昌拌粉",
      ],
    };
  },
  created() {
    this.Height = {
      height: window.innerHeight + "px",
    };
  },
  methods: {

    // 开始循环
    hanldEating() {
      this.isWhile = true;
      this.setim();
    },

    // 暂停循环
    hanldStop() {
      this.isWhile = false;
      this.setim()
    },

    // 处理菜谱循环
    setim() {
      let timer = null;
      let idx = 0
      if (this.isWhile) {
        timer = setInterval(() => {
          this.foodName = this.foodMenu[idx];
          if (idx < this.foodMenu.length) {
            idx++;
          } else {
            idx = 0;
          }
        }, 50);
      } else {
        // 清除所有定时器
        let end = setInterval(function () { }, 10000);
        for (let i = 1; i <= end; i++) {
            clearInterval(i);
        }
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
  background: url('../assets/body-bg.jpg') no-repeat;
  background-size: 100% 100%;
  .eat-header {
    text-align: center;
    font-size: 30px;
    font-weight: bold;
    letter-spacing: 2px;
    color: #333;
  }
  .eat-body {
    .eat-name {
      height: 50px;
      line-height: 50px;
      text-align: center;
      font-weight: bold;
      font-size: 18px;
    }
    .eat-btn {
      width: 100px;
      line-height: 40px;
      text-align: center;
      font-size: 14px;
      border: 1px solid #888;
      background: rgba(0, 0, 0, 0.6);
      cursor: pointer;
      color: #fff;
    }
  }
  .eat-footer {
      width: 100%;
      text-align: center;
      position: absolute;
      bottom: 12px;
      background: rgba(0, 0, 0, 0.6);
      color: #fff;
  }
}

@media screen and (max-width: 760px){
    .eat-container {
        background-size: auto 100%;
        background-position-x: -250px;
    }
}
</style>