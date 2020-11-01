<template>
  <div class="dashboard-editor-container">
    <!-- 我希望左边是消息右边是代办 -->

    <!-- 标签页 -->
    <el-row :gutter="32">
      <el-col :span="16">
        <div class="grid-content bg-purple">
          <el-tabs
            v-model="activeName"
            @tab-click="handleClick"
            :style="{ height: screen + 'px' }"
            class="group1 group2"
            size="large"
          >
            <el-tab-pane
              v-for="(menu, index) in menus"
              :key="menu.title"
              :name="menu.title"
            >
              <span slot="label">
                <i :class="coins[index]"></i>
                {{ menu.title }}
              </span>
              <!-- <div v-if="clickOne(index)">
          {{ current }}
        </div> -->
              <div>
                {{ menu.title }}
              </div>
              <div></div>
            </el-tab-pane>
          </el-tabs>
        </div>
      </el-col>
      <el-col :span="8">
        <div class="grid-content bg-purple">
          <!-- 封装成组件 -->
          <el-card class="box-card" :style="{ height: screen + 'px' }">
            <div slot="header" class="clearfix">
              <span>代办</span>
              <!-- <el-button style="float: right; padding: 3px 0" type="text"
                >操作按钮</el-button
              > -->
            </div>
            <div v-for="o in 4" :key="o" class="text item">
              {{ "列表内容 " + o }}
            </div>
          </el-card>
        </div>
      </el-col>
    </el-row>

    <!-- <div :style="{position: 'relative',left:width/2.4+ 'px',height: height/2+ 'px',width: width/2.7 + 'px'}" class="group1">
  scss
  </div>  -->

    <el-row :gutter="32">
      <!-- <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <raddar-chart />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <pie-chart />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <bar-chart />
        </div>
      </el-col> -->
    </el-row>
  </div>
</template>

<script>
export default {
  name: "Index",
  components: {},
  data() {
    return {
      menus: menus,
      width: window.screen.availWidth,
      height: window.screen.availHeight,
      activeName: "全部",
      current: "",
      coins: coins,
      screen: document.body.clientHeight - 180,
    };
  },
  mounted() {
    let _that = this;
    window.onresize = () => {
      return (() => {
        _that.screen = document.body.clientHeight - 180;
      })();
    };
  },
  methods: {
    clickOne(index) {
      if (index == 0) {
        this.current = "全部消息";
        return true;
      } else if (index == 1) {
        this.current = "审批消息";
        return true;
      } else if (index == 2) {
        this.current = "通知消息";
        return true;
      }
      return false;
    },
    handleClick(tab, event) {
      console.log(tab, event);
    },
  },
};
const menus = [
  {
    title: "全部",
  },
  {
    title: "审批",
  },
  {
    title: "通知",
  },
];
const coins = ["el-icon-menu", "el-icon-s-check", "el-icon-s-comment"];
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }

  .group1 {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }

  .group3 {
    position: relative;
  }
}

// @media (max-width:1024px) {
//   .chart-wrapper {
//     padding: 8px;
//   }
// }
</style>

<style scoped>
.group2 >>> .el-tabs__item {
  font-size: 16px;
  padding: 0 30px;
}
</style>




