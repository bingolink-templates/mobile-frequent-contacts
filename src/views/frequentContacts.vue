<template>
  <div ref="wrap">
    <!-- 常用联系人 -->
    <div class="frequent-contacts">
      <div class="frequent-contacts-title flex">
        <text class="f28 fw5 c0">常用联系人</text>
        <text class="f24 c153 fw4 pl20 pt10 pb10" @click="frequentContactMoreEvent">全部</text>
      </div>
      <div class="frequent-contacts-content flex">
        <div v-for="(item, index) in frequentContactArr" :key='index' @click='frequentContactUserEvent'>
          <bui-image src="/image/test.jpg" radius='34px' width="68px" height="68px" @click='frequentContactUserEvent'>
          </bui-image>
          <text class="f26 c102 fw4 mt16">张珊珊</text>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        frequentContactArr: ['', '', '', '']
      }
    },
    methods: {
      // 更多
      frequentContactMoreEvent() {
        this.$alert()
      },
      // 常用联系人
      frequentContactUserEvent() {
        this.$alert()
      },
      broadcastWidgetHeight() {
        let _params = this.$getPageParams();
        setTimeout(() => {
          dom.getComponentRect(this.$refs.wrap, (ret) => {
            var channel = new BroadcastChannel('WidgetsMessage')
            channel.postMessage({
              widgetHeight: ret.size.height,
              id: _params.id
            });
            channel.close();
          });
        }, 100)
      }
    },
    mounted() {
      this.broadcastWidgetHeight()
    }
  }
</script>

<style lang="css" src="../css/common.css"></style>
<style>
  .main {}

  .frequent-contacts {
    background-color: #fff;
  }

  .frequent-contacts-title {
    height: 40px;
    margin: 18px 23px 20px 25px;
  }

  .frequent-contacts-content {
    margin: 40px 62px 44px 62px;
  }
</style>