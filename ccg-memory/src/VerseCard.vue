<template>
  <el-card class="verse-card"
           :body-style="{'flex-grow': 1, 'display': 'flex', 'flex-flow': 'column nowrap'}">
    <div slot="header">
      <a class="verse-ref" :href="'http://esv.to/' + verse.reference">{{ verse.reference }}</a>
      <small class="date">{{ verse.start }}</small>
    </div>
    <div class="verse-text">

      <transition name="fade">
          <span v-if="withContext"
                class="verse-pre"
          >
            {{ verse.pre }}
          </span>
      </transition>

      <span class="verse">{{ verse.text }}</span>

      <transition name="fade">
        <span v-if="withContext"
              class="verse-post"
        >
          {{ verse.post }}
        </span>
      </transition>
    </div>
    <div
      v-if="verse.pre || verse.post"
      @click="withContext = !withContext"
      class="context-control"
    >
      <i v-if="!withContext" class="el-icon-caret-bottom"></i>
      <i v-if="withContext" class="el-icon-caret-top"></i>
    </div>
  </el-card>
</template>

<script>
  export default {
    props: ['verse'],
    data() {
      return {
        withContext: false
      }
    }
  }
</script>

<style lang="scss">
  /*None-scoped element overrides*/
  @import "themify";

  .el-card__header {
    @include themify($themes) {
      border-bottom: themed('cardBorders');
    }
  }
</style>
<style lang="scss" scoped>
  @import "themify.scss";

  .verse-card {
    display: flex;
    flex-flow: column nowrap;
    @include themify($themes) {
      color: themed('textColor');
      background-color: themed('backgroundColor');
    }
  }

  .verse-ref {
    font-weight: bold;
    text-decoration: none;
    @include themify($themes) {
      color: themed('textColor');
    }
  }

  .date {
    float: right;
    @include themify($themes) {
      color: themed('altTextColor');
    }
  }

  .verse-text {
    flex-grow: 1;
    float: left;
    font-size: 1.2rem;
    text-rendering: optimizeLegibility;
    font-family: 'Spectral', serif;
    font-kerning: normal;
  }

  .verse-pre, .verse, .verse-post {
    display: inline;
  }

  .verse-pre, .verse-post {
    @include themify($themes) {
      color: themed('altTextColor');
    }
  }

  .context-control {
    margin-top: 14px;
    margin-bottom: -20px;
    height: 35px;
    line-height: 35px;
    width: 100%;
    text-align: center;
    align-self: flex-end;
    cursor: pointer;
    @include themify($themes) {
      color: themed('altTextColor');
      border-top: themed('cardBorders');
    }
  }

  .context-control:hover {
    color: cornflowerblue;
  }

  /*Transitions for pre,post text showing*/
  .fade-enter-active {
    transition: opacity .4s
  }

  .fade-enter, .fade-leave-to {
    opacity: .05
  }
</style>
