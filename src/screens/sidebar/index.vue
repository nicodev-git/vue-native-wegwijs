<template>
  <nb-container>
    <nb-content class="sidebar-content-wrapper" :bounces="false">
      <nb-list>
        <nb-list-item
          v-for="item in listItems"
          :key="item.id"
          :class="selectedItem===item.id?'selected':''"
          button
          style="padding-left: 10; margin-left: -5; padding-top: 10; padding-bottom: 10"
          :onPress="() => handleListItemClick(item.id)"
        >
          <nb-left>
            <image :source="selectedItem===item.id?item.icon:item.activeIcon" style="width: 40; height: 40; margin-right: 10"/>
            <nb-text :class="selectedItem===item.id?'selected':''" style="font-size: 14">
              {{ item.title }}
            </nb-text>
          </nb-left>
        </nb-list-item>
      </nb-list>
    </nb-content>
  </nb-container>
</template>

<script>
// Load item images
import home from "../../../assets/home.png"
import icon1 from "../../../assets/icon1.png"
import icon2 from "../../../assets/icon2.png"
import icon3 from "../../../assets/icon3.png"
import icon4 from "../../../assets/icon4.png"
import icon5 from "../../../assets/icon5.png"
import icon6 from "../../../assets/icon6.png"
import icon7 from "../../../assets/icon7.png"
import icon8 from "../../../assets/icon8.png"
import icon9 from "../../../assets/icon9.png"
import icon1_hover from "../../../assets/icon1_hover.png"
import icon2_hover from "../../../assets/icon2_hover.png"
import icon3_hover from "../../../assets/icon3_hover.png"
import icon4_hover from "../../../assets/icon4_hover.png"
import icon5_hover from "../../../assets/icon5_hover.png"
import icon6_hover from "../../../assets/icon6_hover.png"
import icon7_hover from "../../../assets/icon7_hover.png"
import icon8_hover from "../../../assets/icon8_hover.png"
import icon9_hover from "../../../assets/icon9_hover.png"

export default {
  props: {
    navigation: {
      type: Object
    }
  },
  data() {
    return {
      selectedItem: 0,
      listItems: [
        {
          "id": 0,
          "title": "Welkom",
          "icon": home,
          "activeIcon": home
        },
        {
          "id": 1,
          "title": "NIEUWS",
          "icon": icon1,
          "activeIcon": icon1_hover
        },
        {
            "id": 2,
            "title": "GIDS",
            "icon": icon2,
            "activeIcon": icon2_hover
        },
        {
            "id": 3,
            "title": "ACTIVITEITEN & IDEEËN",
            "icon": icon3,
            "activeIcon": icon3_hover
        },
        {
            "id": 4,
            "title": "FINANCIËEN",
            "icon": icon4,
            "activeIcon": icon4_hover
        },
        {
            "id": 5,
            "title": "GEZOND LEVEN",
            "icon": icon5,
            "activeIcon": icon5_hover
        },
        {
            "id": 6,
            "title": "WELZIJN & ONDERSTEUNING",
            "icon": icon6,
            "activeIcon": icon6_hover
        },
        {
            "id": 7,
            "title": "ONTMOETEN",
            "icon": icon7,
            "activeIcon": icon7_hover
        },
        {
            "id": 8,
            "title": "OPGROEIEN & OPVOEDEN",
            "icon": icon8,
            "activeIcon": icon8_hover
        },
        {
            "id": 9,
            "title": "HULP IN HUIS",
            "icon": icon9,
            "activeIcon": icon9_hover
        }
      ]
    };
  },
  methods: {
    handleListItemClick(id) {
      this.selectedItem = id;
      if(id === 0) {
        this.navigation.navigate('Home');
      } else {
        this.navigation.navigate('NewsList');
      }
    }
  }
};
</script>

<style>
.sidebar-content-wrapper {
  flex: 1;
  background-color: #fff;
  padding-top: 50;
}
.drawer-cover {
  flex: 1;
  align-self: stretch;
  position: relative;
  margin-bottom: 10;
}
.selected {
  color: white;
  background-color: #494c23;
}
.list-item-badge-container {
  border-radius: 3;
  height: 25;
  width: 72;
}
.list-item-badge-text {
  /* font-weight: 400; // not-working  */
  /* font-weight: bold; // working */
  text-align: center;
}
</style>
