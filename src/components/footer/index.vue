<template>
  <view class="search-bar">
    <text-input class="search-bar__input"></text-input>
    <nb-button
      transparent
    >
      <image :source="searchIcon" class="search-button"/>
    </nb-button>
  </view>
</template>

<script>
import searchIcon from "../../../assets/search.png";

export default {
  data() {
    return {
      searchIcon
    }
  }
};
</script>

<style>
.search-bar {
  width: 100%;
  padding-top: 10;
  height: 55;
  margin-bottom: 50;
  padding-left: 20;
  padding-right: 20;
  display: flex;
  align-items: center;
  flex-direction: row;
}
.search-bar__input {
  flex: 1;
  height: 50;
  background-color: white;
  font-size: 20;
  padding-left: 10;
  padding-right: 10;
}
.search-button {
  width: 50;
  height: 50;
}
</style>
