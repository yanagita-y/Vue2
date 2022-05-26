<template>
<div>
  <div class="form">
    <div class="header">
      <p id="step">STEP4</p>
      <p id="inst">以下の内容をご確認ください</p>
    </div>
    <div class="body">
      <p class="genre">-性別-</p>
      <p>{{ gender }}</p>
    </div>
    <div class="body">
      <p class="genre">-生年月日-</p>
      <p>{{ year }}年{{ month }}月{{ day }}日</p>
    </div>
    <div class="body">
      <p class="genre">-現在、生命保険に加入されていますか？-</p>
      <p>{{ question1 }}</p>
    </div>
    <div class="body">
      <p class="genre">-現在入院中ですか。または、最近3ヶ月以内に医師の診察・検査の結果、入院・手術をすすめられたことはありますか？-</p>
      <p>{{ question2 }}</p>
    </div>
    <div class="body">
      <p class="genre">-過去5年以内に、病気やけがで、手術をうけたことまたは継続して7日以上の入院をしたことがありますか？-</p>
      <p>{{ question3 }}</p>
    </div>
    <div class="body">
      <p class="genre">-ご相談内容-</p>
      <p>{{ step3Text }}</p>
    </div>
  </div>
  <div class="button-group">
    <router-link to="/questionnaire2" class="button">＜ 前へ戻る</router-link>
    <router-link to="/questionnaire3" class="button">送信</router-link>
  </div>
</div>
</template>
<script>
  export default {
    computed:{
      gender : function() {
        return this.$store.getters.gender
      },
      year : function() {
        return this.$store.getters.year
      },
      month : function() {
        return this.$store.getters.month
      },
      day : function() {
        return this.$store.getters.day
      },
      question1 : function() {
        return this.$store.getters.question1
      },
      question2 : function() {
        return this.$store.getters.question2
      },
      question3 : function() {
        return this.$store.getters.question3
      },
      step3Text : function() {
        return this.$store.getters.step3Text;
      }
    }
  }
</script>
