<template>
  <div>
    <h1>📖 Memory Verses</h1>
    <div class="grid">
      <verse-card class="verse-card"
        v-for="verse in orderedVerses"
        :key="verse.start"
        :verse="verse"
      ></verse-card>
    </div>
  </div>
</template>

<script>
  import VerseCard from './VerseCard.vue';

  export default {
    name: 'app',
    components: {
      'verse-card': VerseCard
    },
    data() {
      return {
        withContext: false,
        verses: [{
          start: new Date(2017, 10, 5).toDateString(),
          reference: '2 Timothy 3:16-17',
          pre: "",
          text: 'All scripture is breathed out by God and is profitable for teaching, for reproof, for correction, and for training in righteousness, that the man of God may be complete, equipped for every good work.',
          post: ""
        }, {
          start: new Date(2017, 10, 12).toDateString(),
          reference: 'Galatians 2:20',
          pre: 'For through the law I died to the law, so that I might live to God.',
          text: 'I have been crucified with Christ, it is no longer I who live, but Christ who lives in me. And the life I now live in the flesh I live by faith in the Son of God, who loved me and gave himself for me.',
          post: 'I do not nullify the grace of God, for if righteousness were through the law, then Christ died for no purpose.'
        }, {
          start: new Date(2017, 10, 19).toDateString(),
          reference: 'John 5:39-20',
          pre: '[Jesus talking to the pharisees] And the Father who sent me has himself borne witness about me. His voice you have never heard, his form you have never seen, and you do not have his word abiding in you, for you do not believe the one whom he has sent.',
          text: 'You search the Scriptures because you think that in them you have eternal life; and it is they that bear witness about me, yet you refuse to come to me that you may have life.',
          post: ''
        }, {
          start: new Date(2017, 10, 26).toDateString(),
          reference: 'Colossians 3:16-17',
          pre: 'Put on then, as God\'s chosen ones, holy and beloved, compassionate hearts, kindness, humility, meekness, and patience, bearing with one another and, if one has a complaint against another, forgiving each other; as the Lord has forgiven you, so you also must forgive. And above all these put on love, which binds everything together in perfect harmony. And let the peace of Christ rule in your hearts, to which indeed you were called in one body. And be thankful.',
          text: 'Let the word of Christ dwell in you richly, teaching and admonishing one another in all wisdom, singing psalms and hymns and spiritual songs, with thankfulness in your hearts to God. And whatever you do, in word or deed, do everything in the name of the Lord Jesus, giving thanks to God the Father through him.',
          post: 'Wives, submit to your husbands, as is fitting in the Lord. Husbands, love your wives, and do not be harsh with them.'
        }, {
          start: new Date(2017, 11, 3).toDateString(),
          reference: 'Isaiah 55:8-9',
          pre: 'Seek the Lord while he may be found; call upon him while he is near; let the wicked forsake his way, and the unrighteous man his thoughts; let him return to the Lord, that he may have compassion on him, and to our God, for he will abundantly pardon.',
          text: 'For my thoughts are not your thoughts, neither are your ways my ways, declares the Lord. For as the heavens are higher than the earth, so are my ways higher than your ways and my thoughts than your thoughts.',
          post: ""
        }]
      }
    },
    computed: {
      orderedVerses() {
        return this.verses.reverse();
      }
    }
  }
</script>

<style scoped>

  .grid {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-around;
  }

  .verse-card {
    position: relative;
    margin-top: 15px;
    flex: 1 1 100%;
  }


  @media (min-width: 780px) {
    .verse-card {
      flex: 0 1 48%;
    }
  }

  @media (min-width: 1239px) {
    .verse-card {
      flex: 0 1 31%;
    }
  }

  @media (min-width: 1365px) {
    .verse-card {
      flex: 0 1 23%
    }
  }
</style>
