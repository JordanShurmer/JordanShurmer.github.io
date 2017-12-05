<template>
  <div id="app">
    <h1>📖 Memory Verses</h1>
    <div class="grid">
      <template v-for="verse in verses">
        <el-card>
          <div slot="header">
            <a class="card-head" :href="'http://esv.to/' + verse.reference">{{ verse.reference }}</a>
            <small style="float: right;">{{ verse.start }}</small>
          </div>
          <p>{{ verse.text }}</p>
        </el-card>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      verses: [{
        start: new Date(2017, 10, 5).toDateString(),
        reference: '2 Timothy 3:16-17',
        text: 'All scripture is breathed out by God and is profitable for teaching, for reproof, for correction, and for training in righteousness, that the man of God may be complete, equipped for every good work.'
      }, {
        start: new Date(2017, 10, 12).toDateString(),
        reference: 'Galatians 2:20',
        text: 'I have been crucified with Christ, it is no longer I who live, but Christ who lives in me. And the life I now live in the flesh I live by faith in the Son of God, who loved me and gave himself for me.'
      }, {
        start: new Date(2017, 10, 19).toDateString(),
        reference: 'John 5:39-20',
        text: 'You search the Scriptures because you think that in them you have eternal life; and it is they that bear witness about me, yet you refuse to come to me that you may have life.'
      }, {
        start: new Date(2017, 10, 26).toDateString(),
        reference: 'Colossians 3:16-17',
        text: 'Let the word of Christ dwell in you richly, teaching and admonishing one another in all wisdom, singing psalms and hymns and spiritual songs, with thankfulness in your hearts to God. And whatever you do, in word or deed, do everything in the name of the Lord Jesus, giving thanks to God the Father through him.'
      }, {
        start: new Date(2017, 11, 4).toDateString(),
        reference: 'Isaiah 55:8-9',
        text: 'For my thoughts are not your thoughts, nor are your ways My ways," declares the Lord. For as high as the heavens are higher than the earth, So are My ways higher than your ways and My thoughts than your thoughts.'
      }]
    }
  }
}
</script>

<style>
  @import url("https://fonts.googleapis.com/css?family=Spectral");

  html {
    box-sizing: border-box
  }
  *, *::before, *::after {
    box-sizing: inherit
  }

  body {
    font-family: 'Spectral', serif;
  }

  .grid {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-around;
  }

  .card-head {
    font-weight: bold;
    color: initial;
    text-decoration: none;
  }

  .el-card {
    margin-top: 15px;
    flex: 1 1 100%;
  }

  .el-card small {
    color: rgba(1, 1, 1, .4);
  }

  @media (min-width: 780px) {
    .el-card {
      flex: 0 1 48%;
    }
  }

  @media (min-width: 1239px) {
    .el-card {
      flex: 0 1 31%;
    }
  }

  @media (min-width: 1365px) {
    .el-card {
      flex: 0 1 23%
    }
  }
</style>
