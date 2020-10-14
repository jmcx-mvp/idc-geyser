<template>
  <div class="dashboard-container">
    <div class="row">
      <div class="col text-center">
        <img class="home-logo" :src="'/static/logo/logo.png'" alt=""/>
      </div>
    </div>
    <div class="row">
      <div class="col text-center welcome-tit">{{ $t("common.welcome") }}</div>
    </div>
    <div class="row">
      <div class="col text-center welcome-txt">{{ $t("common.welcomeTxt") }}</div>
    </div>

    <div class="row">
      <div class="col-xl-4 col-lg-4 col-md-4 col-sm-12 col-xs-12 text-center"
           v-for="(product, index) in products" :key="index">
        <product :product-data="product" :product-index="index"></product>
      </div>
    </div>

    <loading :active.sync="loading"
             :can-cancel="false"
             :is-full-page="true"></loading>
  </div>
</template>

<script>
import Product from "./Product";
import Loading from 'vue-loading-overlay';
import 'vue-loading-overlay/dist/vue-loading.css';

export default {
  name: "dashboard",
  components: { Product, Loading },

  data() {
    return {
      allBalance: null,
      poolInfo: null,
      loading: false,

      products: [
        {
          img: "/static/actions/transfer.png",
          name: "First Pool!",
          txt: "Deposit IDC-ETH LP Earn IDC",
          tx: "IDC-ETH-POOL1",
          apy: "3000",
          stat: false,
          dateTime: "2020-09-20 12:00:00",
        },
        {
          img: "/static/actions/transfer.png",
          name: "Second Pool!",
          txt: "Deposit IDC-ETH LP Earn IDC",
          tx: "IDC-ETH-POOL2",
          apy: "2000",
          stat: false,
          dateTime: "2020-10-01 10:00:00",
        },
        {
          img: "/static/actions/transfer.png",
          name: "Third Pool!",
          txt: "Deposit IDC-ETH LP Earn IDC",
          tx: "IDC-ETH-POOL3",
          apy: "1000",
          stat: false,
          dateTime: "2020-10-21 15:00:00",
        },
      ]
    }
  },

  methods: {
    seeTheMenu() {
      this.$router.push({name: "Dashboard"})
    },
  },
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
@import "../../styles/colors.scss";
@import "../../styles/fonts.scss";

.dashboard-container {
  width: 100%;
  height: 100%;

  .home-logo{
    width: 120px;
    height: 120px;
  }

  .welcome-tit {
    font-size: 27px;
    color: $fontColor;
    letter-spacing: 2px;
    font-family: $fontTit;
  }
  .welcome-txt {
    margin-bottom: 30px !important;
    color: $txtColor;
    font-family: $fontTxt;
  }
}
</style>
