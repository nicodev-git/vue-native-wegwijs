<template>
  <nb-container :style="{ backgroundColor: '#939751' }">
    <Header :navigation="this.props.navigation" back="Home"/>
    <nb-content padder>
      <Calendar
        :current="selectedDate"
        :markedDates="getMarkedDates(selectedDate)"
        :onDayPress="onChange"
      />
      <nb-text v-if="selectedDate" class="selected-date">{{selectedDate}}</nb-text>
      <view v-if="item">
        <touchable-opacity
          v-for="post in item.post"
          :key="post.id"
          :onPress="() => this.props.navigation.navigate('NewsDetail')"
        >
          <nb-card class="news-card" >
            <nb-card-item>
              <nb-body>
                <nb-text class="published-date">Gepubliceerd {{post.published_date}}</nb-text>
                <nb-text class="post-title">{{post.title}}</nb-text>
              </nb-body>
            </nb-card-item>
            <nb-card-item>
              <nb-body>
                <nb-text class="post-desc">{{getSubString(post.description)}}</nb-text>
              </nb-body>
            </nb-card-item>
          </nb-card>
        </touchable-opacity>
      </view>
    </nb-content>
  </nb-container>
</template>

<script>
import Header from '../../components/header'
// import DateTimePicker from '@react-native-community/datetimepicker'
import { Calendar } from "react-native-calendars"

const dummyData = [
  {
    "id": "1",
    "title": "NIEUWS",
    "description": "Korte omschrijving op deze plek",
    "post": [
      {
        "id": "1",
        "published_date": "12-05-2021",
        "title": "Brandweer op zoek naar nieuwe leden",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      },
      {
        "id": "2",
        "published_date": "12-05-2021",
        "title": "Denk mee over de buitenruimte in Zevenaar",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      }
    ]
  },
  {
    "id": "1",
    "title": "NIEUWS",
    "description": "Korte omschrijving op deze plek",
    "post": [
      {
        "id": "1",
        "published_date": "12-05-2021",
        "title": "Brandweer op zoek naar nieuwe leden",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      }
    ]
  },
  {
    "id": "1",
    "title": "NIEUWS",
    "description": "Korte omschrijving op deze plek",
    "post": [
      {
        "id":"3",
        "published_date": "12-05-2021",
        "title": "Denk mee over de buitenruimte in Zevenaar",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      }
    ]
  },
  {
    "id": "1",
    "title": "NIEUWS",
    "description": "Korte omschrijving op deze plek",
    "post": [
      {
        "id": "2",
        "published_date": "12-05-2021",
        "title": "Denk mee over de buitenruimte in Zevenaar",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      },
      {
        "id":"3",
        "published_date": "12-05-2021",
        "title": "Denk mee over de buitenruimte in Zevenaar",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      }
    ]
  },
  {
    "id": "1",
    "title": "NIEUWS",
    "description": "Korte omschrijving op deze plek",
    "post": [
      {
        "id": "1",
        "published_date": "12-05-2021",
        "title": "Brandweer op zoek naar nieuwe leden",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      },
      {
        "id": "2",
        "published_date": "12-05-2021",
        "title": "Denk mee over de buitenruimte in Zevenaar",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      },
      {
        "id":"3",
        "published_date": "12-05-2021",
        "title": "Denk mee over de buitenruimte in Zevenaar",
        "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
      }
    ]
  }
]

export default {
  components: {
    Header,
    // DateTimePicker,
    Calendar
  },
  methods: {
    onChange: function (date) {
      this.selectedDate = date.dateString
      this.item = dummyData[Math.floor(Math.random()*4)]
    },
    getSubString: function(string) {
      const LIMIT = 100;
      if (string.length > LIMIT)
          return string.substring(0, LIMIT) + "...";
      else return string;
    },
    getMarkedDates: function(date) {
      return {[date]: {selected: true, selectedColor: 'blue'}}
    }
  },
  data() {
    return {
      selectedDate: null,
      item: null
    };
  }
};
</script>

<style>
.category-title {
  margin-top: 10;
  font-weight: bold;
  text-transform: capitalize;
  width: 100%;
  color: white;
}
.selected-date {
  width: 100%;
  margin-top: 10;
  margin-bottom: 20;
  border-radius: 15;
  overflow: hidden;
  background-color: #494c23;
  color: white;
  padding: 10;
  text-align: center;
}
.category-desc {
  color: white;
  margin-bottom: 20;
}
.published-date {
  margin-top: 5;
  color: #919845;
}
.post-title {
  color: #494c23;
  font-weight: bold;
  font-size: 18;
}
.news-item {
  padding-left: 0;
  margin: 0;
  border-width: 0;
}
.news-card {
  border-radius: 15; 
  overflow: hidden;
}
.post-desc {
  color: #494c23;
}
.card-item-image {
  width: 100%;
  height: 200;
}
</style>