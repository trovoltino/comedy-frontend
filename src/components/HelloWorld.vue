<template>
  <div class="posts">
    <div>here will be twitter posts</div>
    <button type="button" @click="getTweets">Show Tweets</button>
    <ul class="tweet-list">
      <p class="links" v-for="tweet in tweets" v-bind:key="tweet">{{tweet}}</p>
    </ul>
  </div>
</template>

<script>

import axios from 'axios';

//const url = 'http://localhost:5000/tweet';
const liveUrl = 'https://comedy-backend.herokuapp.com/tweet';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    async getTweets(err) {
      try {
        const res = await axios.get(liveUrl);
        this.tweets = res['data'];
      } catch {
        console.log(err);
      }
    }
  },
  data() {
    return{
      show: false,
      current:0,
      tweets: []
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
