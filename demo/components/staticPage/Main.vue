<template>
  <div class="page has-navbar" v-nav="{title: '首页-静态', showBackButton: true}"
       v-tabbar="{'menus': menus, menuColor: '#999', activeMenuColor: '#FF4400', onMenuClick: menuClicked}">
    <div class="page-content padding-top">
      <p v-if="show == 0">
        <MainHome></MainHome>
      </p>
      <p class="text-center" v-if="show == 1">Discount</p>
      <div class="text-center" v-if="show == 2">
        <p>Cart</p>
        <button class="button button-assertive" @click="updateBadge(2)">update badge</button>
      </div>
      <p v-if="show == 3">
        <Me></Me>
      </p>
    </div>
  </div>
</template>
<script>

  import MainHome from "./MainHome";
  import Me from "./Me";
  export default {
    components: {Me, MainHome},
    data() {
      return {
        menus: [
          {
            iconOn: 'ion-ios-home',
            iconOff: 'ion-ios-home',
            text: '首页',
          },
          {
            iconOn: 'ion-ios-pricetags',
            iconOff: 'ion-ios-pricetags',
            text: '折扣',
          },
          {
            iconOn: 'ion-ios-cart',
            iconOff: 'ion-ios-cart',
            text: '购物车',
            badge: 5
          },
          {
            iconOn: 'ion-ios-person',
            iconOff: 'ion-ios-person',
            text: '我的',
          }
        ],
        show: 0
      }
    },

    methods: {
      menuClicked(menuIndex) {
        this.show = menuIndex
      },

      updateBadge(menuIndex) {
        $tabbar.$emit('updateTabbarBadge', menuIndex, this.menus[menuIndex].badge++)
      }
    },

    beforeDestroy() {
      $tabbar.$emit('hideTabbar')
    }
  }
</script>
