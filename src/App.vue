<template>
  <div id="app" class="container pt-5">
    <div class="text-center">
      <div class="row">
        <div class="col-12">
          <h1 class="display-3">ダミー電話番号生成器</h1>
        </div>
      </div>
      <p>現在使用されていない携帯電話の番号を自動生成します。記入例やテスト等にどうぞ。</p>
      <div class="row form-group">
        <div class="input-group col-md-6 offset-md-3">
          <input type="text" v-model="dummy_phone_number" class="form-control form-control-lg">
          <div class="input-group-append">
            <button class="btn btn-primary" type="button" v-on:click="generate">再生成</button>
          </div>
        </div>
      </div>
    </div>
    <hr />
    <div class="qa">
      <p class="lead">どうやって生成しているの？</p>
      <p>総務省公式サイトの<a href="http://www.soumu.go.jp/main_sosiki/joho_tsusin/top/tel_number/number_shitei.html" target="_blank">電気通信番号指定状況
  </a>から、電気通信事業者がまだ割り当てられていない部分を抽出して生成しています。使う際は自己責任でお願いします。</p>
      <p class="lead">いつのデータ？</p>
      <p>最終更新日時：平成30年5月19日</p>
    </div>
  </div>
</template>
<script>
const unusedPhoneIndexs = require('./data.json')

export default {
  name: 'app',
  data () {
    return {
      dummy_phone_number: ''
    }
  },
  methods: {
    generate: function () {
      const index = this.arrayShuffle(unusedPhoneIndexs)[0]
      this.dummy_phone_number = `${index}${this.randomNum()}`
    },
    arrayShuffle: function(a) {
      for (let i = a.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [a[i], a[j]] = [a[j], a[i]];
      }
      return a;
    },
    randomNum: function(){
      const min = 10000
      const max = 99999
      return Math.floor( Math.random() * (max + 1 - min) ) + min
    }
  },
  created: function () {
    this.generate()
  }
}
</script>

<style lang="scss">
body {
  background-color: #f5f5f5;
}
.qa {
  font-size: 12px;
}
</style>
