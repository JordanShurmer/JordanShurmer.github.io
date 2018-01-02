<template>
  <div id="app" :class="`theme-${activeTheme}`">
    <div class="app-container">

      <div class="header">
        <h1 class="title">📖 Memory Verses</h1>
        <theme-picker class="themes" v-model="activeTheme"></theme-picker>
      </div>

      <div class="grid">
        <verse-card class="verse-card"
                    v-for="verse in orderedVerses"
                    :key="verse.start"
                    :verse="verse"
        ></verse-card>
      </div>

    </div>
  </div>
</template>

<script>
  import VerseCard from './VerseCard.vue';
  import ThemePicker from './ThemePicker.vue';

  export default {
    name: 'app',
    components: {
      'verse-card': VerseCard,
      'theme-picker': ThemePicker,
    },
    data() {
      return {
        activeTheme: 'light',
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
        }, {
          start: new Date(2017, 11, 10).toDateString(),
          reference: 'Hebrews 1:3-4',
          pre: 'Long ago, at many times and in many ways, God spoke to our fathers by the prophets, but in these last days he has spoken to us by his Son, whom he appointed the heir of all things, through whom also he created the world.',
          text: 'He is the radiance of the glory of God and the exact imprint of his nature, and he upholds the universe by the word of his power. After making purification for sins, he sat down at the right hand of the Majesty on high, having become as much superior to angels as the name he has inherited is more excellent than theirs.',
          post: 'For to which of the angels did God ever say, “You are my Son, today I have begotten you”?'
        }, {
          start: new Date(2017, 11, 17).toDateString(),
          reference: 'Psalm 127:2',
          pre: 'Unless the Lord builds the house, those who build it labor in vain. Unless the Lord watches over the city, the watchman stays awake in vain.',
          text: 'It is in vain that you rise up early and go late to rest, eating the bread of anxious toil; for he gives to his beloved sleep.',
          post: '',
        }, {
          start: new Date(2017, 11, 24).toDateString(),
          reference: 'Isaiah 9:6',
          pre: '',
          text: 'For to us a child is born, to us a son is given; and the government shall be upon his shoulder, and his name shall be called Wonderful Counselor, Mighty God, Everlasting Father, Prince of Peace.',
          post: 'Of the increase of his government and of peace there will be no end, on the throne of David and over his kingdom, to establish it and to uphold it with justice and with righteousness from this time forth and forevermore. The zeal of the Lord of hosts will do this.',
        }, {
          start: new Date(2017, 11, 31).toDateString(),
          reference: '2 Corinthians 5:21',
          pre: '',
          text: 'For our sake he made him to be sin who knew no sin, so that in him we might become the righteousness of God.',
          post: '',
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

<style lang="scss" scoped>
  @import "themify.scss";

  .app-container {
    position: absolute;
    top: 0;
    left: 0;
    min-width: 100%;
    min-height: 100%;
    padding-bottom: 14px;

    @include themify($themes) {
      background-color: themed('backgroundColor');
      color: themed('textColor');
    }

    .header {
      display: flex;
      flex-flow: row wrap;
      align-items: center;
      justify-content: space-between;

      .title {
        font-size: 2em;
        line-height: 2em;
      }

      .themes {
        width: 1.5em;
        height: 1.5em;
        margin-right: 25px;
        align-self: center;
      }
    }

    .grid {
      display: flex;
      flex-flow: row wrap;
      justify-content: space-around;
      width: 95%;
      margin: auto;
    }

    .verse-card {
      position: relative;
      margin-top: 15px;
      flex: 1 1 100%;
      @include themify($themes) {
        border: themed('cardBorders');
        box-shadow: themed('boxShadow');
      }
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

  }
</style>
