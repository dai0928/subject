<template>

<div>
  <div class="top_countor">
    <p>Counter:{{ count }}</p>
    <button class="btn1" @click="addForm()" v-on:click="plus">追加</button>
    <button class="btn1" @click="deleteForm()">リセット</button>
  </div>
  <div class="textbox">
    <input v-model="motherText1" class="text">
    <input v-model.number="motherText2" type="number" class="text1">
  </div>
  <div v-for="(text, index) in text1" :key="index" id='2' class="addBox">
    <input class="text" v-model="text1[index]">
    <input class="text1" type="number" v-model.number="text2[index]">
    <!-- v-model.numberとすることでint型での値を取得 -->
    <!-- indexを書かないと、書かなかった方のフォームの文字がそれ以降すべて同じになる（固有のidが存在しなくなるから？） -->
    <!-- 上記と同じ理由で両方text1にすると、生成されたフォームの文字列が一緒になる（indexが1の2つ、2の2つ...のようになる） -->
  </div>
  <div>
    <h1 class="top_title">fixTempDLog: false</h1>
    <div class="menu_list_top">
      <p style="left: 10px;">編集</p>
      <p style="left: 300px;">Dessert(100g serving)</p>
      <p style="left: 500px;">Calories</p>
      <p style="left: 650px;">Fat(g)</p>
      <p style="left: 800px;">Carbs(g)</p>
      <p style="left: 950px;">Protein(g)</p>
      <p style="left: 1100px;">Iron(%)</p>
    </div>
    <div class="menu_list" v-show="list1">
      <!-- data()でshowをtrueにすることで表示可能 -->
      <transition>
        <div class="modal_back" v-show="modal1">
          <div class="modal_main">
            <p class="modal_text">name</p>
            <textarea class="modal_input" type="text" v-model="dessert1"></textarea>
            <p class="modal_text">calories</p>
            <textarea class="modal_input" v-model="calories1"></textarea>
            <button class="close_modal" v-on:click="modal1 = !modal1">編集完了</button>
          </div>
        </div>
      </transition>
      <button class="btn_update" v-on:click="modal1 = !modal1">編集</button>
      <button class="btn_delete" v-on:click="list1 = !list1">削除</button> 
      <!-- 〇〇 = !〇〇 で、trueからfalseに代わり、表示されなくなる -->
      <p class="Dessert">{{ dessert1 }}</p>
      <p class="Calories">{{ calories1 }}</p>
      <p class="Fat">0.2</p>
      <p class="Carbs">22.5</p>
      <p class="Protein">1.1</p>
      <p class="Iron">0.3</p>
    </div>
    <div class="menu_list" v-show="list2">
      <!-- data()でshowをtrueにすることで表示可能 -->
      <transition>
        <div class="modal_back" v-show="modal2">
          <div class="modal_main">
            <p class="modal_text">name</p>
            <textarea class="modal_input" type="text" v-model="dessert2"></textarea>
            <p class="modal_text">calories</p>
            <textarea class="modal_input" v-model="calories2"></textarea>
            <button class="close_modal" v-on:click="modal2 = !modal2">編集完了</button>
          </div>
        </div>
      </transition>
      <button class="btn_update" v-on:click="modal2 = !modal2">編集</button>
      <button class="btn_delete" v-on:click="list2 = !list2">削除</button> 
      <!-- 〇〇 = !〇〇 で、trueからfalseに代わり、表示されなくなる -->
      <p class="Dessert">{{ dessert2 }}</p>
      <p class="Calories">{{ calories2 }}</p>
      <p class="Fat">0.1</p>
      <p class="Carbs">16</p>
      <p class="Protein">0.4</p>
      <p class="Iron">0.1</p>
    </div>
    <div class="menu_list" v-show="list3">
      <!-- data()でshowをtrueにすることで表示可能 -->
      <transition>
        <div class="modal_back" v-show="modal3">
          <div class="modal_main">
            <p class="modal_text">name</p>
            <textarea class="modal_input" type="text" v-model="dessert3"></textarea>
            <p class="modal_text">calories</p>
            <textarea class="modal_input" v-model="calories3"></textarea>
            <button class="close_modal" v-on:click="modal3 = !modal3">編集完了</button>
          </div>
        </div>
      </transition>
      <button class="btn_update" v-on:click="modal3 = !modal3">編集</button>
      <button class="btn_delete" v-on:click="list3 = !list3">削除</button> 
      <!-- 〇〇 = !〇〇 で、trueからfalseに代わり、表示されなくなる -->
      <p class="Dessert">{{ dessert3 }}</p>
      <p class="Calories">{{ calories3 }}</p>
      <p class="Fat">0.1</p>
      <p class="Carbs">15</p>
      <p class="Protein">0.2</p>
      <p class="Iron">0</p>
    </div>
    <div class="menu_list" v-show="list4">
      <!-- data()でshowをtrueにすることで表示可能 -->
      <transition>
        <div class="modal_back" v-show="modal4">
          <div class="modal_main">
            <p class="modal_text">name</p>
            <textarea class="modal_input" type="text" v-model="dessert4"></textarea>
            <p class="modal_text">calories</p>
            <textarea class="modal_input" v-model="calories4"></textarea>
            <button class="close_modal" v-on:click="modal4 = !modal4">編集完了</button>
          </div>
        </div>
      </transition>
      <button class="btn_update" v-on:click="modal4 = !modal4">編集</button>
      <button class="btn_delete" v-on:click="list4 = !list4">削除</button> 
      <!-- 〇〇 = !〇〇 で、trueからfalseに代わり、表示されなくなる -->
      <p class="Dessert">{{ dessert4 }}</p>
      <p class="Calories">{{ calories4 }}</p>
      <p class="Fat">19</p>
      <p class="Carbs">6</p>
      <p class="Protein">2.5</p>
      <p class="Iron">0.7</p>
    </div>
    <div class="menu_list" v-show="list5">
      <!-- data()でshowをtrueにすることで表示可能 -->
      <transition>
        <div class="modal_back" v-show="modal5">
          <div class="modal_main">
            <p class="modal_text">name</p>
            <textarea class="modal_input" type="text" v-model="dessert5"></textarea>
            <p class="modal_text">calories</p>
            <textarea class="modal_input" v-model="calories5"></textarea>
            <button class="close_modal" v-on:click="modal5 = !modal5">編集完了</button>
          </div>
        </div>
      </transition>
      <button class="btn_update" v-on:click="modal5 = !modal5">編集</button>
      <button class="btn_delete" v-on:click="list5 = !list5">削除</button> 
      <!-- 〇〇 = !〇〇 で、trueからfalseに代わり、表示されなくなる -->
      <p class="Dessert">{{ dessert5 }}</p>
      <p class="Calories">{{ calories5 }}</p>
      <p class="Fat">0.1</p>
      <p class="Carbs">11.8</p>
      <p class="Protein">0.9</p>
      <p class="Iron">0.2</p>
    </div>
    <div class="menu_list" v-show="list6">
      <!-- data()でshowをtrueにすることで表示可能 -->
      <transition>
        <div class="modal_back" v-show="modal6">
          <div class="modal_main">
            <p class="modal_text">name</p>
            <textarea class="modal_input" type="text" v-model="dessert6"></textarea>
            <p class="modal_text">calories</p>
            <textarea class="modal_input" v-model="calories6"></textarea>
            <button class="close_modal" v-on:click="modal6 = !modal6">編集完了</button>
          </div>
        </div>
      </transition>
      <button class="btn_update" v-on:click="modal6 = !modal6">編集</button>
      <button class="btn_delete" v-on:click="list6 = !list6">削除</button> 
      <!-- 〇〇 = !〇〇 で、trueからfalseに代わり、表示されなくなる -->
      <p class="Dessert">{{ dessert6 }}</p>
      <p class="Calories">{{ calories6 }}</p>
      <p class="Fat">0.1</p>
      <p class="Carbs">14</p>
      <p class="Protein">1</p>
      <p class="Iron">0.3</p>
    </div>
    <div class="menu_list" v-show="list7">
      <!-- data()でshowをtrueにすることで表示可能 -->
      <transition>
        <div class="modal_back" v-show="modal7">
          <div class="modal_main">
            <p class="modal_text">name</p>
            <textarea class="modal_input" type="text" v-model="dessert7"></textarea>
            <p class="modal_text">calories</p>
            <textarea class="modal_input" v-model="calories7"></textarea>
            <button class="close_modal" v-on:click="modal7 = !modal7">編集完了</button>
          </div>
        </div>
      </transition>
      <button class="btn_update" v-on:click="modal7 = !modal7">編集</button>
      <button class="btn_delete" v-on:click="list7 = !list7">削除</button> 
      <!-- 〇〇 = !〇〇 で、trueからfalseに代わり、表示されなくなる -->
      <p class="Dessert">{{ dessert7 }}</p>
      <p class="Calories">{{ calories7 }}</p>
      <p class="Fat">0.2</p>
      <p class="Carbs">15</p>
      <p class="Protein">1</p>
      <p class="Iron">0.3</p>
    </div>
    <div class="menu_list" v-show="list8">
      <!-- data()でshowをtrueにすることで表示可能 -->
      <transition>
        <div class="modal_back" v-show="modal8">
          <div class="modal_main">
            <p class="modal_text">name</p>
            <textarea class="modal_input" type="text" v-model="dessert8"></textarea>
            <p class="modal_text">calories</p>
            <textarea class="modal_input" v-model="calories8"></textarea>
            <button class="close_modal" v-on:click="modal8 = !modal8">編集完了</button>
          </div>
        </div>
      </transition>
      <button class="btn_update" v-on:click="modal8 = !modal8">編集</button>
      <button class="btn_delete" v-on:click="list8 = !list8">削除</button> 
      <!-- 〇〇 = !〇〇 で、trueからfalseに代わり、表示されなくなる -->
      <p class="Dessert">{{ dessert8 }}</p>
      <p class="Calories">{{ calories8 }}</p>
      <p class="Fat">0.1</p>
      <p class="Carbs">16.9</p>
      <p class="Protein">0.6</p>
      <p class="Iron">0.2</p>
    </div>
  </div>
  

</div>

</template>

<script>
export default {
  
  data() {
    return {
      count: 0,
      motherText1: '',
      motherText2: 0,
      text1: [],
      text2: [0],
      list1: true,
      modal1: false,
      dessert1: "Banana",
      calories1: "86",
      list2: true,
      modal2: false,
      dessert2: "Grape",
      calories2: "59",
      list3: true,
      modal3: false,
      dessert3: "Apple",
      calories3: "54",
      list4: true,
      modal4: false,
      dessert4: "Avocado",
      calories4: "186",
      list5: true,
      modal5: false,
      dessert5: "Orange",
      calories5: "48",
      list6: true,
      modal6: false,
      dessert6: "Kiwi",
      calories6: "53",
      list7: true,
      modal7: false,
      dessert7: "cherry",
      calories7: "60",
      list8: true,
      modal8: false,
      dessert8: "Mango",
      calories8: "68",
    }
  },
    // v-modelを引っ張ってきて元の状態を定義する
  methods: {
    plus() {
      let sum = 0;
      // forで増やしたフォームの２番目の列のみ回収
      for ( let i = 0; i < this.text2.length; i++) {
        sum += this.text2[i]
      }
      console.log(typeof(this.motherText2));
      // for文を抜けた後のsumがなぜかstr型になるので再びint(number)型に変換
      this.count = Number(sum) + this.motherText2

    },
    addForm() { 
      // this.text2をいじるとフォームを増やすコードが動かなくなるので、計算の関数は独立して記述
      this.text1.push(''),
      this.text2.push('')
    },
    deleteForm() {
      this.count = 0
      this.motherText1 = '',
      this.motherText2 = '',
      this.text1.splice("all"),
      this.text2.splice("all")
    },

  },

}

</script>

<style>

  html,body {
      width: 100%;
      height: 100%; 
  }
  * {
      margin: 0;
      padding: 0;
  }



  .top_countor {
    text-align: center;
    margin: 0;
  }
  .btn1 {
    height: 40px;
    padding: 10px;
    width: auto;
    border: none;
    box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.8);
    transition: all 0.2s;
  }
  .btn1:hover {
    background-color: rgba(0, 0, 0, 0.5);
  }



  .textbox {
    width: 100%;
    float: left;
    text-align: center;
  }
  .text, .text1 {
    width: 49%;
    height: 30px;

  }
  .addBox {
    display: ;
    text-align: center;
  }



  .menu_list_top {
    display: flex;
    border-bottom: solid 1px rgba(0, 0, 0, 0.5);
    width: 100%;
    font-weight: 550;
    padding-bottom: 5px;
   
  }
  .menu_list_top p {
    position: relative;
  }
  .top_title{
    margin-top:70px;
    text-align: center;
    font-weight: 1;
  }



  .menu_list {
    display: flex;
    border-bottom: solid 1px rgba(0, 0, 0, 0.5);
    width: 100%;
    padding-bottom: 5px;
    padding-top: 5px;
  }
  .menu_list:hover{
    background-color: rgba(0, 0, 0, 0.1);
  }
  .btn_update{
    margin-left: 0.5%;
    padding: 5px 10px; 
    color: red;
    background: none;
    border-color: red;
    border-radius: 5px;
    transition: 0.25s;
  }
  .btn_update:hover {
    background-color: rgba(255, 0, 0, 0.2);
  }
 .btn_delete{
    margin-left: 0.3%;
    padding: 5px 10px;
    border-radius: 5px;
    color: rgba(0, 130, 255, 1);
    background: none;
    border-color: rgba(0, 130, 255, 0.6);
    transition: 0.25s;
  }
  .btn_delete:hover {
    background-color: rgba(0, 130, 255, 0.2);
  }



  .v-enter {
    opacity: 0;
  }
  .v-enter-to {
    opacity:1;
  }
  .v-enter-active {
    transition: opacity 0.3s ease-out;
  }
  .v-leave {
    opacity: 1;
  }
  .v-leave-to {
    opacity:0;
  }
  .v-leave-active {
    transition: opacity 0.3s ease-out;
  }
  .modal_back{
    z-index: 1;
    position: fixed;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.5);
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .modal_main {
    text-align: center;
    background-color: white;
    height: 400px;
    width: 500px;
    padding: 10px;
    box-shadow: 5px 5px 10px 5px rgba(0, 0, 0, 0.5);
  }
  .modal_text {
    margin-top: 2%;
    font-weight: 550;
  }
  .modal_input {
    height: 25%;
    width: 95%;
    padding: 10px;
    font-size: 15px;
  }
  .close_modal {
    position: relative;
    background: none;
    border-color: rgba(0, 130, 255, 0.6);
    padding: 5px 10px;
    color: rgba(0, 130, 255, 1);
    top: 10%;
    float: right;
    border-radius: 5px;
  }
  .close_modal:hover {
    background-color: rgba(0, 0, 0, 0.1);
  }
  .Dessert {
    position: absolute;
    left: 330px;
  }
  .Calories {
    position: absolute;
    left: 720px;
  }
  .Fat {
    position: absolute;
    left: 940px;
  }
  .Carbs {
    position: absolute;
    left: 1145px;

  }
  .Protein {
    position: absolute;
    left: 1365px;
  }
  .Iron {
    position: absolute;
    left: 1605px;
  }
</style>
