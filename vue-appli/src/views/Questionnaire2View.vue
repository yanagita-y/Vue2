<template>
<div>
  <div class="form">
    <div class="header">
      <p id="step">STEP3</p>
      <p id="inst">ご相談内容をご記入ください</p>
    </div>
    <div class="body">
      <p class="genre">-ご相談内容-</p>
        <label><textarea type="textarea" name="q3" cols="100%" rows="40" value="" @change="updateGender"></textarea>></label>
    </div>
  </div>
  <div class="button-group">
    <router-link to="/questionnaire" class="button">＜ 前へ戻る</router-link>
    <router-link to="/questionnaire2" class="button">次へ進む ＞</router-link>
  </div>
</div>
</template>
