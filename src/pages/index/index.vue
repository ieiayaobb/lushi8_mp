<template>
  <div class="container">
    <div v-for="chairman in chairmans" :key="chairman.id">
      <card :thumb="chairman.img" :href="chairman.href" :name="chairman.name" :num="chairman.num"></card>
    </div>
  </div>
</template>

<script>
import Card from '../../components/card'
import 'wx-promise-pro'

export default {
  data () {
    return {
      chairmans: []
    }
  },

  components: {
    Card
  },

  created () {
    // 调用应用实例的方法获取全局数据
    // this.getUserInfo()
    wx.pro.request({
      url: 'https://lushiba.leanapp.cn/api/chairmans/',
      data: {},
      method: 'GET',
      header: {'content-type': 'application/json'}
    }).then(res => {
      this.chairmans = res.data
    }).catch(err => {
      console.log(err)
    }).finally(() => {
      // wx.hideLoading()
    })
  }
}
</script>

<style scoped>

.form-control {
  display: block;
  padding: 0 12px;
  margin-bottom: 5px;
  border: 1px solid #ccc;
}
</style>
