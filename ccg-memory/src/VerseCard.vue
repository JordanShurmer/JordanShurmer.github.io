<template>
  <el-card class="verse-card"
           :body-style="{'flex-grow': 1, 'display': 'flex', 'flex-flow': 'column nowrap'}">
    <div class="card-head" slot="header">
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

<style scoped>

  .verse-card {
    display: flex;
    flex-flow: column nowrap;
  }

  .verse-ref {
    font-weight: bold;
    color: black;
    text-decoration: none;
  }

  .date {
    float: right;
    color: rgba(1, 1, 1, .4);
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
    color: rgba(0, 0, 0, .425);
  }

  .context-control {
    margin-top: 14px;
    margin-bottom: -20px;
    height: 35px;
    line-height: 35px;
    width: 100%;
    border-top: 1px solid #e6ebf5;
    text-align: center;
    align-self: flex-end;
    color: rgba(0, 0, 0, .2);
    cursor: pointer;
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
