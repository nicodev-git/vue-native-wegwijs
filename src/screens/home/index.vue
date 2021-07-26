<template>
  <nb-container :style="{ backgroundColor: '#939751' }">
    <Header :navigation="this.props.navigation"/>
    <nb-content padder> 
      <view class="item-grid">
        <CategoryItem v-for="item in listItems" :data="item" :navigation="this.props.navigation"/>
      </view>
    </nb-content>
    <Footer/>
  </nb-container>
</template>

<script>
import Header from '../../components/header'
import Footer from '../../components/footer'
import CategoryItem from '../../components/item'

// Load item images
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
  components: {
    Header,
    Footer,
    CategoryItem
  },
  data() {
    return {
      listItems: [
        {
          "id": "1",
          "title": "NIEUWS",
          "icon": icon1,
          "activeIcon": icon1_hover
        },
        {
            "id": "2",
            "title": "GIDS",
            "icon": icon2,
            "activeIcon": icon2_hover
        },
        {
            "id": "3",
            "title": "ACTIVITEITEN & IDEEËN",
            "icon": icon3,
            "activeIcon": icon3_hover,
            "url": "Activity"
        },
        {
            "id": "4",
            "title": "FINANCIËEN",
            "icon": icon4,
            "activeIcon": icon4_hover
        },
        {
            "id": "5",
            "title": "GEZOND LEVEN",
            "icon": icon5,
            "activeIcon": icon5_hover
        },
        {
            "id": "6",
            "title": "WELZIJN & ONDERSTEUNING",
            "icon": icon6,
            "activeIcon": icon6_hover
        },
        {
            "title": "ONTMOETEN",
            "icon": icon7,
            "activeIcon": icon7_hover
        },
        {
            "title": "OPGROEIEN & OPVOEDEN",
            "icon": icon8,
            "activeIcon": icon8_hover
        },
        {
            "title": "HULP IN HUIS",
            "icon": icon9,
            "activeIcon": icon9_hover
        }
      ]
    };
  }
};
</script>

<style>
.body-icon-color {
  color: #999;
}
.item-grid {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  padding-top: 20;
  padding-bottom: 30;
}
.item-wrapper {
  height: 160;
  width: 120;
  margin: 5;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
</style>