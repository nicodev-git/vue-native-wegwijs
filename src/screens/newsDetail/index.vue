<template>
  <nb-container :style="{ backgroundColor: '#939751' }">
    <Header :navigation="this.props.navigation" back="NewsList"/>
    <nb-content padder> 
      <nb-h2 class="category-title">
        {{item.title}}
      </nb-h2>
      <nb-text class="category-desc">
        {{item.description}}
      </nb-text>
      <nb-card class="news-card">
        <nb-card-item>
          <nb-body>
            <nb-text class="published-date">Gepubliceerd {{item.post.published_date}}</nb-text>
            <nb-text class="post-title">{{item.post.title}}</nb-text>
          </nb-body>
        </nb-card-item>

        <nb-card-item cardBody style="padding-left: 15; padding-right: 15;">
          <image
            :source="item.post.image"
            class="card-item-image"
          />
        </nb-card-item>
        <nb-card-item>
          <nb-body>
            <nb-text class="post-desc">{{item.post.description}}</nb-text>
          </nb-body>
        </nb-card-item>
      </nb-card>
    </nb-content>
  </nb-container>
</template>

<script>
import Header from '../../components/header'
import newsImage from "../../../assets/news.png";

export default {
  components: {
    Header
  },
  data() {
    return {
      item: {
        "id": "1",
        "title": "NIEUWS",
        "description": "Korte omschrijving op deze plek",
        "post": {
          "id": "1",
          "published_date": "12-05-2021",
          "title": "Brandweer op zoek naar nieuwe leden",
          "image": newsImage,
          "description": "Zevenaar - Diverse brandweerposten in de regio zijn dringend op zoek naar nieuwe leden. Zowel mannen als vrouwen kunnen hiervoor in aanmerking komen. Ben je be nieuwd wat het inhoudt om een brandweer man/-vrouw te zijn en wat je daarvoor moet doen? Kijk dan op bijdebrandweer.nl voor informatie"
        }
      }
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