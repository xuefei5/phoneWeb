<template>
<div class="page has-navbar" v-nav="{title: '商城', showBackButton: true}">
  <div class="page-content padding-top">
    <!--  搜索--开始 -->
    <div class="bar bar-header item-input-inset">
      <label class="item-input-wrapper">
        <i class="icon ion-ios-search placeholder-icon"></i>
        <form action='' :id="formId" >
          <input ref="input" type="search" :placeholder="placeholder" :value="value" @change="updateValue($event.target.value)">
        </form>
      </label>
    </div>
    <!--  搜索--结束 -->
    <!--滑动栏--开始 -->
    <swipe ref="mySwipe" style='height:15em ;margin:0 auto'>
      <swipe-item><img src="../../../assets/images/hyIndex1.jpg" style="max-width:100%;height:auto;"></swipe-item>
      <swipe-item><img src="../../../assets/images/hyIndex2.jpg" style="max-width:100%;height:auto;"></swipe-item>
      <swipe-item><img src="../../../assets/images/hyIndex3.jpg" style="max-width:100%;height:auto;"></swipe-item>
    </swipe>
    <div style="display: none">
      <img src="../../../assets/images/pidan.jpg">
      <img src="../../../assets/images/mihoutao.jpg">
    </div>
    <!--滑动栏--结束 -->

    <div class="item item-divider">
      热门商品
    </div>
    <cells :items="shopOffers" row="2" col="2" :outerBorder="false" style="background-color: #f5f5f5"></cells>
  </div>
</div>
</template>

<script>
  export default {
    props: {
      value: {
        type: String,
        required: true
      },
      placeholder: {
        type: String,
        default: '请输入商品名称'
      },
      onSearch: Function,
      onCancel: Function
    },

    data() {
      return {
        formId: 'von-search-' + Math.random().toString(36).substring(3, 6),
        shopOffers:[
          '<div style="background-color: white"><img src="/dist/pidan.jpg" style="width: 10em;height: 10em"/><div>【湖北特产】松花鸭皮蛋...<p style="color: red"><span style="float: left;margin-left: 15px">￥:29.90</span>  <i class="icon ion-ios-cart-outline" style="float: right;margin-right: 15px"></i></p></div></div>',
          '<div><img src="/dist/mihoutao.jpg" style="width: 10em;height: 10em"/><div>【四川特产】四川浦江猕猴...<p style="color: red"><span style="float: left;margin-left: 15px">￥:59.90</span>  <i class="icon ion-ios-cart-outline" style="float: right;margin-right: 15px"></i></p></div></div>',
          '<div><img src="/dist/pidan.jpg" style="width: 10em;height: 10em"/><div>【湖北特产】松花鸭皮蛋...<p style="color: red"><span style="float: left;margin-left: 15px">￥:29.90</span>  <i class="icon ion-ios-cart-outline" style="float: right;margin-right: 15px"></i></p></div></div>',
          '<div><img src="/dist/mihoutao.jpg" style="width: 10em;height: 10em"/><div>【四川特产】四川浦江猕猴...<p style="color: red"><span style="float: left;margin-left: 15px">￥:59.90</span>  <i class="icon ion-ios-cart-outline" style="float: right;margin-right: 15px"></i></p></div></div>',
          ]
      }
    },

    mounted() {
      document.getElementById(this.formId).onsubmit = this.search;
      this.initSwip();
    },

    methods: {
      search(e) {
        e.preventDefault()
        let search = document.querySelector('#' + this.formId + ' > [type=search]')
        search.blur()
        if (this.onSearch) this.onSearch()
      },
      updateValue(value) {
        this.$refs.input.value = value,
          this.$emit('input', value)
      },
      initSwip(){
        const con_this= this;
        setInterval(function(){ con_this.$refs.mySwipe.next() }, 3000);
      }
    }
  }
</script>

<style scoped>

</style>
