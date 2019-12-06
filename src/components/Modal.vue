<template>
  <div class="mask">
    <div class="modal-container">
      <div class="block">
        <span>抽奖最大人数（到场人数）：</span>
        <input v-model="maxNo">
      </div>
      <div class="block">
        <span>五等奖（充电宝）内定：</span>
        <input v-for="(item, index) in stage1Nums" v-model="stage1Nums[index]" :key="index">
      </div>
      <div class="block">
        <span>四等奖（体重秤）内定：</span>
        <input v-for="(item, index) in stage2Nums" v-model="stage2Nums[index]" :key="index">
      </div>
      <div class="block">
        <span>三等奖（电水壶）内定：</span>
        <input v-for="(item, index) in stage3Nums" v-model="stage3Nums[index]" :key="index">
      </div>
      <div class="block">
        <span>二等奖（吹风机）内定：</span>
        <input v-for="(item, index) in stage4Nums" v-model="stage4Nums[index]" :key="index">
      </div>
      <div class="block">
        <span>一等奖（电饭煲）内定：</span>
        <input v-model="stage5Num[0]">
      </div>
      <div class="block btn-container">
        <div class="btn btn-confirm" @click="handleConfirm()">确定</div>
        <div class="btn btn-cancel" @click="handleCancel()">取消</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    maxNum: '',
    list: Array
  },
  data () {
    return {
      maxNo: this.maxNum,
      stage1Nums: [this.list[0], this.list[1], this.list[2], this.list[3], this.list[4]],
      stage2Nums: [this.list[5], this.list[6], this.list[7], this.list[8]],
      stage3Nums: [this.list[9], this.list[10], this.list[11]],
      stage4Nums: [this.list[12], this.list[13]],
      stage5Num: [this.list[14]]
    }
  },
  computed: {
  },
  watch: {
  },
  mounted () {
  },
  destroyed () {
  },
  methods: {
    handleConfirm () {
      let data = {
        maxNum: this.maxNum,
        stage1Nums: this.stage1Nums,
        stage2Nums: this.stage2Nums,
        stage3Nums: this.stage3Nums,
        stage4Nums: this.stage4Nums,
        stage5Num: this.stage5Num
      }
      this.$emit('confirmed', data)
    },
    handleCancel () {
      this.$emit('calcelled')
    }
  }
}
</script>

<style lang="scss">
.mask {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, .5);
  .modal-container {
    width: 500px;
    padding: 50px;
    margin: 20px auto;
    background: #fff;
    border-radius: 10px;
    .block {
      margin: 10px 0;
      input {
        width: 50px;
        margin-right: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;
      }
    }
    .btn-container {
      text-align: center;
      .btn {
        display: inline-block;
        padding: 5px 10px;
        border-radius: 5px;
        cursor: pointer;
      }
      .btn-confirm {
        background: #42b983;
        color: #fff;
      }
      .btn-cancel {
        background: #eee;
      }
    }
  }
}
</style>
