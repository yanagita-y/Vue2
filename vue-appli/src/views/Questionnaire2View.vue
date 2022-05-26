<template>
<div>
  <div class="form">
    <div class="header">
      <p id="step">STEP3</p>
      <p id="inst">ご相談内容をご記入ください</p>
    </div>
    <div class="body">
      <p class="genre">-ご相談内容-</p>
        <label><textarea type="textarea" v-model="step3Text" cols="100%" rows="40" value="" ></textarea>></label>
    </div>
  </div>
  <div class="button-group">
    <router-link to="/questionnaire" class="button">＜ 前へ戻る</router-link>
    <router-link to="/questionnaire3" class="button">次へ進む ＞</router-link>
  </div>
</div>
</template>
<script>
  export default {
    computed:{
    step3Text:{
      get() {
        return this.$store.getters.step3Text;
      },
      set(value) {
        this.$store.dispatch('getStep3Text', value);
      }
    },
  }
}
</script>
