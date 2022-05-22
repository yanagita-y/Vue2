<template>
<div>
  <div class="form">
    <div class="header">
      <p id="step">STEP2</p>
      <p id="inst">以下にお答えください</p>
    </div>
    <div class="body" v-if="currentQuestion>=1">
      <p class="genre">現在、生命保険に加入されていますか？</p>
        <label><input type="radio" v-model="question1" value="はい" v-on:click="currentQuestion++">はい</label>
        <label><input type="radio" v-model="question1" value="いいえ" v-on:click="currentQuestion++">いいえ</label>
      </div>
    <div class="body" v-if="question1">
      <p class="genre">現在入院中ですか。または、最近3ヶ月以内に医師の診察・検査の結果、入院・手術をすすめられたことはありますか？</p>
        <label><input type="radio" v-model="question2" value="はい" v-on:click="currentQuestion++">はい</label>
        <label><input type="radio" v-model="question2" value="いいえ" v-on:click="currentQuestion++">いいえ</label>
      </div>
    <div class="body" v-if="question2">
      <p class="genre">過去5年以内に、病気やけがで、手術をうけたことまたは継続して7日以上の入院をしたことがありますか？</p>
        <label><input type="radio" v-model="question3" value="はい" v-on:click="currentQuestion++">はい</label>
        <label><input type="radio" v-model="question3" value="いいえ" v-on:click="currentQuestion++">いいえ</label>
    </div>
  </div>
  <div class="button-group">
    <router-link to="/" class="button">＜ 前へ戻る</router-link>
    <router-link to="/questionnaire2" class="button">次へ進む ＞</router-link>
  </div>
</div>
</template>
<script>
  export default {
    data: function() {
      return {
        currentQuestion:1
      }
    },
    computed:{
    question1:{
      get() {
        return this.$store.state.question1;
      },
      set(value) {
        this.$store.dispatch('getQuestion1', value);
      }
    },
    question2:{
      get() {
        return this.$store.state.question2;
      },
      set(value) {
        this.$store.dispatch('getQuestion2', value);
      }
    },
    question3:{
      get() {
        return this.$store.state.question3;
      },
      set(value) {
        this.$store.dispatch('getQuestion3', value);
      }
    },
    methods:{
      nextButton:function() {
        this.currentQuestion++;
        if(this.currentQuestion > 3){
          this.currentQuestion =3;
        }
      }
    }
  }
}
</script>