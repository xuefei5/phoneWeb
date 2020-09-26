<template>
  <div class="page-content">
    <div class="item item-divider">
      当前热卖
    </div>
    <swipe ref="mySwipe" style='height:15em ;margin:0 auto'>
      <swipe-item><img src="../../assets/images/caomei.jpg" style="max-width:100%;height:auto;"></swipe-item>
      <swipe-item><img src="../../assets/images/pingguo.jpg" style="max-width:100%;height:auto;"></swipe-item>
      <swipe-item><img src="../../assets/images/dangao.jpg" style="max-width:100%;height:auto;"></swipe-item>
    </swipe>
    <div class="item item-divider">
      链接跳转
    </div>
    <cells :items="entrances" :on-cell-click="onCellClick" row="2" col="4" :outerBorder="false"></cells>
    <div class="item item-divider">
      商品分类
    </div>
    <div class="padding light-bg">
      <button-bar theme="assertive" :tab-items="promotions" :tab-index="promotionIndex"
                  :on-tab-click="index => promotionIndex = index">
      </button-bar>
    </div>
    <div class="item item-borderless">
      <p v-if="promotionIndex === 0">
        <cells :items="offer.offer1" :on-cell-click="onCellClick" row="1" col="3" :outerBorder="false"></cells>
      </p>
      <p v-if="promotionIndex === 1">
        <cells :items="offer.offer2" :on-cell-click="onCellClick" row="1" col="3" :outerBorder="false"></cells>
      </p>
    </div>
    <div class="item item-divider">
      热门商品
    </div>
    <cells :items="shopOffers" :on-cell-click="onCellClick" row="2" col="2" :outerBorder="false"></cells>
    <div class="item item-divider" style="text-align: center">
      ----我也是有底线的----
    </div>
    <div class="item item-divider"></div>
  </div>
</template>

<script>
    export default {
      name: "MainHome",
      data(){
          return{
            promotions: ["往期热卖", "抢购进行中"],
            promotionIndex: 0,
            entrances: [
              '<div class="entrance assertive"><i class="icon ion-heart"></i><br><span>热门商品</span></div>',
              '<div class="entrance energized"><i class="icon ion-ios-star"></i><br><span>选择2</span></div>',
              '<div class="entrance balanced"><i class="icon ion-ios-location"></i><br><span>选择3</span></div>',
              '<div class="entrance positive"><i class="icon ion-pie-graph"></i><br><span>选择4</span></div>',
              '<div class="entrance assertive"><i class="icon ion-contrast"></i><br><span>选择5</span></div>',
              '<div class="entrance energized"><i class="icon ion-paintbucket"></i><br><span>选择6</span></div>',
              '<div class="entrance assertive"><i class="icon ion-tshirt"></i><br><span>选择7</span></div>',
              '<div class="entrance balanced"><i class="icon ion-thumbsup"></i><br><span>选择8</span></div>'
            ],
            offer:{
              offer1:[
                '苹果',
                "橘子",
                "石榴"
              ],
              offer2:[
                "香蕉",
                "鸭梨",
                "葡萄"
              ]
            },
            shopOffers:[
              '<div><img src="/dist/caomei.jpg" style="width: 10em;height: 10em"/><div>草莓：￥:20元 <p style="color: red" @click="onCellClick">订购</p></div></div>',
              '<div><img src="/dist/caomei.jpg" style="width: 10em;height: 10em"/><div>苹果：￥:50元 <p style="color: red" @click="onCellClick">订购</p></div></div>',
              '<div><img src="/dist/caomei.jpg" style="width: 10em;height: 10em"/><div>草莓：￥:20元 <p style="color: red" @click="onCellClick">订购</p></div></div>',
              '<div><img src="/dist/caomei.jpg" style="width: 10em;height: 10em"/><div>苹果：￥:50元 <p style="color: red" @click="onCellClick">订购</p></div></div>',
              '<div><img src="/dist/caomei.jpg" style="width: 10em;height: 10em"/><div>草莓：￥:20元 <p style="color: red" @click="onCellClick">订购</p></div></div>',
              '<div><img src="/dist/caomei.jpg" style="width: 10em;height: 10em"/><div>苹果：￥:50元 <p style="color: red" @click="onCellClick">订购</p></div></div>',
              '<div><img src="/dist/caomei.jpg" style="width: 10em;height: 10em"/><div>草莓：￥:20元 <p style="color: red" @click="onCellClick">订购</p></div></div>',
              '<div><img src="/dist/caomei.jpg" style="width: 10em;height: 10em"/><div>苹果：￥:50元 <p style="color: red" @click="onCellClick">订购</p></div></div>',
            ]
          }
      },
      methods:{
        onCellClick(cellIndex) {
          $dialog.alert({
            theme: 'ios',
            title: '提示',
            content: '王顺是个智障',
            okText: '是的'
          }).then(() => {
            console.log('alert hide.')
          })
        }
      }

    }
</script>

<style scoped>

</style>
