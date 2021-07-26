<template>
  <root>
    <app-navigation></app-navigation>
  </root>
</template>

<script>
import {
  createAppContainer,
  createStackNavigator,
  createDrawerNavigator
} from "vue-native-router";
import { Root } from "native-base";
import HomeScreen from "./screens/home/index.vue";
import SideBarScreen from "./screens/sidebar/index.vue";
import NewsListScreen from "./screens/newsList/index.vue";
import NewsDetailScreen from "./screens/newsDetail/index.vue";
import ActivityScreen from "./screens/activity/index.vue";


const Drawer = createDrawerNavigator(
  {
    Home: { screen: HomeScreen },
    NewsList: { screen: NewsListScreen },
    NewsDetail: { screen: NewsDetailScreen },
    Activity: { screen: ActivityScreen }
  },
  {
    initialRouteName: "Home",
    contentComponent: SideBarScreen
  }
);

const AppNavigation = createAppContainer(
  createStackNavigator(
    {
      Drawer: { screen: Drawer },
      Home: { screen: HomeScreen },
      NewsList: { screen: NewsListScreen },
      NewsDetail: { screen: NewsDetailScreen },
      Activity: { screen: ActivityScreen }
    },
    {
      initialRouteName: "Drawer",
      headerMode: "none"
    }
  )
);
export default {
  components: { Root, AppNavigation }
};
</script>
