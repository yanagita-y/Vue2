<template>
<div>
  <div class="form">
    <div class="header">
      <p id="step">STEP1</p>
      <h1>{{ message }}</h1>
      <p id="inst">お客様の情報を入力してください</p>
    </div>
    <div class="body">
      <p class="genre">-性別-</p>
        <label><input type="radio" v-model="gender" value="男性" @change="updateGender">男性</label>
        <label><input type="radio" v-model="gender" value="女性" @change="updateGender">女性</label>
      <p class="genre">-生年月日-</p>
      <select v-model="year" id="id_year" @change="updateYear">
        <option v-for="(year, key) in years" :key="key">{{ year }}</option>
      </select>年
      <select v-model="month" id="id_month" @change="updateMonth">
        <option v-for="(month, key) in months" :key="key">{{ month }}</option>
      </select>月
      <select v-model="day" id="id_day" @change="updateDay">
        <option v-for="(day, key) in days" :key="key">{{ day }}</option>
      </select>日
    </div>
  </div>
  <div class="button-group">
    <router-link to="/questionnaire" class="button">次へ進む ＞</router-link>
  </div>
</div>
</template>

<script>
const today = new Date();
const this_year = today.getFullYear();

// 配列を変数に格納
const yearList = []
const monthList = []
const dayList = []

// 第一引数〜第二引数までの年月日を生成し、配列（list）に追加する関数を作成
const optionLoop = (start, end, list) => {
    for(let i = start; i <= end; i ++) {
      if(i >= 1000){
        const japaneseCalendar = new Date(i, 1, 1).toLocaleDateString("ja-JP-u-ca-japanese", {year:'numeric'});
        list.push(`${i}年（${japaneseCalendar}）`);
        continue;
      }
      list.push(i);
    }
}
optionLoop(1950, this_year, yearList);
optionLoop(1, 12, monthList);
optionLoop(1, 31, dayList);

// 年月日の値のforループを配列に格納し、vueコンポーネントにexportする
export {yearList, monthList, dayList}

export default {
  data() {
    return {
      years: yearList,
      months: monthList,
      days: dayList,
    }
  },
  computed : {
    gender:{
      get() {
        return this.$store.getters.gender;
      },
      set(value) {
        this.$store.dispatch('getGender', value);
      }
    },
    year:{
      get() {
        return this.$store.getters.year;
      },
      set(value) {
        this.$store.dispatch('getYear', value);
      }
    },
    month:{
      get() {
        return this.$store.getters.month;
      },
      set(value) {
        this.$store.dispatch('getMonth', value);
      }
    },
    day:{
      get() {
        return this.$store.getters.day;
      },
      set(value) {
        this.$store.dispatch('getDay', value);
      },
    },
  },
  methods: {
    updateGender (e) {
      this.$store.commit('updateGender', e.target.value)
    },
    updateYear (e) {
      this.$store.commit('updateYear', e.target.value)
    },
    updateMonth (e) {
      this.$store.commit('updateMonth', e.target.value)
    },
    updateDay (e) {
      this.$store.commit('updateDay', e.target.value)
    },
  }
}
</script>
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
#step{
  background: #1e90ff;
  color: #fff;
  font-size: 2px;
  margin: 0;
  max-width: 40px;
  padding: 2px;
  text-align: center;
}

#inst {
  font-size: 12px;
  color: #696969;
  text-align: center;
  padding-bottom: 10px;
}

.header {
  background: #afeeee;
  margin: 0%;
  padding: 0%;
  line-height: 10px;
  border-bottom: solid 1px #48d1cc;
}

.body {
  font-size: 9px;
  margin: 10px;
  padding-bottom: 10px;
  line-height: 30px;
  text-align: left;
}

.body input {
  vertical-align:middle;
}

.genre {
  color: #1e90ff;
}

select {
  padding: 5px 10px 5px 0px;
  font-size: 9px;
  border: 1px solid #dcdcdc;
}

.form{
  max-width: 80%;
  margin-top: 80px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid #48d1cc;
  border-bottom: 0.5px solid #000;
}

.button-group{
  text-align: center;
}

.button {
  background-color: #40e0d0;
  color: #fff;
  border: solid 1px #48d1cc;
  margin-top: 1rem;
  padding: 5px 10px;
  border-radius: 0.5rem 0.5rem;
  text-decoration: none;
  display:inline-block;
  margin: 10px;
}
</style>