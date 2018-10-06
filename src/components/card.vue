<template>
  <div class="card" @click="jump(href)">
    <img class="thumb-img" :src="thumb" />
    <span class="card-display">
      {{name}}
    </span>
    <span class="card-num">
      {{num}}人
    </span>
  </div>
</template>

<script>
export default {
  props: ['name', 'thumb', 'num', 'href'],
  methods: {
    jump (url) {
      wx.navigateTo({
        url: '/pages/detail/main?url=' + url
      })
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    }
  }
}
</script>

<style>
.card {
  margin: 5px;
  padding: 5px;
  box-shadow: 2px 2px 2px #ccc;
}

.card-display {
  margin: auto;
}

.card-num {
  float: right;
}

.thumb-img {
  width: 40px;
  height: 30px;
}
</style>
