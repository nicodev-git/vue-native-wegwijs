<template>
    <nb-header class="header">
      <nb-left class="header__left">
        <nb-button
          transparent
          :onPress="() => navigation.openDrawer()"
        >
          <nb-icon name="menu" class="header__icon"/>
        </nb-button>
        <nb-button
          v-if="back"
          transparent
          class="back-button"
          :onPress="() => navigation.navigate(back)"
        >
          <nb-icon name="arrow-back" class="header__icon"/>
          <text class="back-text">Vorige</text>
        </nb-button>
      </nb-left>
      <nb-right>
      	<image
   			:source="logo"
        class="logo"
   		/>
      </nb-right>
    </nb-header>
</template>

<script>
import logo from "../../../assets/logo.png";
import hambeger from "../../../assets/hambeger.png";

export default {
  data() {
    return {
      logo,
      hambeger
    };
  },
  props: {
    back: String,
    navigation: Object
  }
};
</script>

<style>
.header {
  height: 70;
  background-color: white;
}
.header__left {
  display: flex;
  flex-direction: row;
  align-items: center;
}
.header__icon {
  color: #4a4b28;
  font-size: 38;
}
.logo {
  width: 160;
  height: 50;
}
.back-button {
  display: flex;
  align-items: center;
}
.back-text {
  font-size: 25;
  font-weight: 600;
  padding-top: 5;
  color: #4a4b28;
  margin: 0;
}
</style>
