<template>
  <div class="text-card">
    <sub-title :title="title"></sub-title>
    <div class="text__card-content">
      <div 
        v-for="(item, index) in textList" 
        :key="index" 
        v-if="textList.length"
        class="text__item">
        <div class="name">{{ item.name }}</div>
        <div class="description">{{ item.description }}</div>
      </div>
      <div class="text__outer-link">
        <a 
          :href="outerLink" 
          target="_blank"
          v-if="outerLink">
          {{ outerLinkName }}
          <img src="~/assets/images/arrow_forward.svg"/>
        </a>
        <div v-else>{{ outerLinkName }}</div>
      </div>
      <wallet-btn 
        :is-active="false" 
        v-if="keyStr === 'wallet'"
        style="margin-top: 14px;">
      </wallet-btn>
    </div>
  </div>
</template>

<script type="text/babel">
import subTitle from '~/components/subTitle';
import walletBtn from './walletBtn';

export default {
  components: {
    subTitle,
    walletBtn
  },
  props: {
    keyStr: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    },
    outerLinkName: {
      type: String,
      default: ''
    },
    outerLink: {
      type: String,
      default: ''
    },
    textList: {
      type: Array,
      default: () => []
    }
  },  
  data: function () {
    return {
    };
  },
  methods: {
    
  }
};
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
@import "~assets/vars";
.text-card {
  font-family:$font-family-title;
  .text__card-content {
    font-size:14px;
    font-weight:600;
    line-height:18px;
    .name {
      margin-top: 18px;
      color:rgba(23,28,52,1);
    }
    .description {
      margin-top: 8px;
      color:rgba(145,154,163,1);
    }
  }
  .text__outer-link {
    margin-top: 15px;
    font-size:16px;
    font-weight:600;
    color:rgba(0,122,255,1);
    line-height:28px;
  }
}
</style>
