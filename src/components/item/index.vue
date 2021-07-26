<template>
  <touchable-opacity
    class="item"
    :style="{width: getResponsiveWidth()}"
    :onPress="() => onItemClick()"
  >
  <view
      :onStartShouldSetResponder="(evt) => true"
      :onMoveShouldSetResponder="(evt) => true"
      :onResponderGrant="onItemClick"
      :onResponderMove="onItemClick"
      :onResponderRelease="onItemRelease"
      class="item"
    >
    <image :source="pressed?data.activeIcon:data.icon" class="item__icon" :style="{width: getResponsiveWidth(), height: getResponsiveWidth()}"/>
    <text class="item__text">{{data.title}}</text>
  </view>
</template>

<script>
import { Dimensions } from 'react-native'

export default {
  data(){
  	return {
  		pressed: false
  	}
  },
  props: {
  	data: Object,
  	navigation: Object
  },
  methods: {
  	onItemClick: function(id) {
      this.pressed = true;
  	},
    onItemRelease: function() {
      this.pressed = false;
      this.navigation.navigate(this.data.url || 'NewsList');
    },
    getResponsiveWidth: function() {
      return Math.round(Dimensions.get('window').width / 3.5);
    }
  }
}
</script>
<style>
.item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  text-align: center;
  margin: 5;
}
.item__icon {
  margin-bottom: 10;
}
.item__text {
  color: white;
  text-align: center;
  font-size: 12.5
}
</style>