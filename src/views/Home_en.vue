<template>
  <div id="app" class="ma-10">
  <div>
     
          <v-toolbar
          class="ma-2"
          color="white"
          height="30px"
          flat
        >
          <v-toolbar-title  class=" text-title-1 font-weight-bold">Voice2People (V2P) estimates what kind of target (age/gender) the text is for and visualizes the directivity of the text.      
          </v-toolbar-title>
        </v-toolbar>

         </v-toolbar>
             <v-toolbar
          class="ml-1 mt-3"
          color="white"
          height="25px"
          flat
        >
          <v-toolbar-title class="text-body-2 font-weight-bold" >Sample Texts       
          </v-toolbar-title>
        </v-toolbar>
  
         <v-row
          class="ma-1">
          
          <v-btn depressed color="blue darken-3" class= "mt-1 mb-2 white--text" type="submit" @click="first_button" >
            1
          </v-btn>
          <v-btn depressed color="pink" class= "ml-3  mt-1 white--text" type="submit" @click="second_button" >
            2
          </v-btn>
          <v-btn depressed color="indigo darken-3" class= "ml-3  mt-1 white--text" type="submit" @click="third_button">
            3
          </v-btn>
          <v-btn depressed color="pink darken-1" class= "ml-3  mt-1 white--text" type="submit" @click="fourth_button">
            4
          </v-btn>
          <v-btn depressed color="deep-purple darken-3" class= "ml-3  mt-1 white--text" @click="fifth_button">
            5
          </v-btn>
          <v-btn depressed color="pink accent-4" class= "ml-3 mt-1 white--text" @click="sixth_button">
            6
          </v-btn>
           <v-btn depressed color="lime darken-3" class= "ml-3 mt-1 white--text"  @click="seventh_button">
            7
          </v-btn>
           <v-btn depressed color="deep-orange darken-3" class= "ml-3  mt-1 white--text" type="submit" @click="eighth_button" >
            8
          </v-btn>
           <v-btn depressed color="cyan darken-4" class= "ml-3  mt-1 white--text" type="submit" @click="nineth_button">
            9
          </v-btn>
          <v-btn depressed color="blue-grey darken-1" class= "ml-3  mt-1 white--text" type="submit" @click="tenth_button">
            10
          </v-btn>
          
          </v-btn>
           </v-row>
        <v-form ref="whole_form">
     <v-textarea
          
            label="Enter text to be analyzed"
            outlined
            ref="form"
            v-model="TextAreaVal"
             :rules="[required]"
          ></v-textarea>
          </v-form>
    </div>
    <v-row
    justify="end"
    align="center"
    class="ma-0.5">
    <v-btn 
    depresse 
    color="blue"
    class="ma-1 mr-3 white--text text--lighten-1"
    type="submit" @click="exec"
    >
      Start Analysis
    </v-btn>
    
    <v-btn
      depressed
      color="red lighten-1"
       class="ma-1 mr-5 white--text text--lighten-1"
       @click="reset"
    >
      Clear
    </v-btn>
   
  </v-row>

    <div >
    <v-toolbar
          class="ma-2"
          color="white"
          height="40px"
          flat>
    
           <v-toolbar-title  class="font-weight-black">Analysis Result</v-toolbar-title>
        </v-toolbar>
    <RadarChart ref="rader_component"/>

    <v-toolbar
          class="mb-1"
          color="white"
          height="280px"
          flat>
    </v-toolbar>

    
    </div>
      
  </div>
</template>

<script>

import RadarChart from "../components/RadarChart.vue";


export default {
  name: "Tool",
  components: {
    RadarChart,
    Social: () => import('@/components/home/Social'),
    
  
  
  },
  data:function() {
        
      return{
      TextAreaVal: '',
      // 入力規則
      required: value => !!value || "Please input text", 
      success: false,}
          
    
  },
  methods: {

      exec(){
        if (this.$refs.whole_form.validate()) {
         this.success = true;
         this.$refs.rader_component.sendAPI(this.TextAreaVal);
      } else {
        this.success = false;
      }
         
      },
      reset () {
        this.$refs.form.reset()
      },
     first_button(){
      // ルフィ
      this.TextAreaVal = 'おれは助けてもらわねェと生きていけねェ自信がある！！！！'
     },
     second_button(){
      // ローラ
      this.TextAreaVal = "努力しなかったら幸せはやってきてはくれないの。失敗して失敗して失敗するからこそ幸せになれる　何が大切なのか分かるんだよ。"
     },
     third_button(){
      // スティーブジョブス　
      this.TextAreaVal = "最も重要な決定とは、何をするかではなく、何をしないかを決めることだ。"
     },
     fourth_button(){
      // 母の日の言葉　
      this.TextAreaVal = "お母さんへ　いつもありがとうございます。日頃の感謝をこめてお花を送ります。 気に入ってくれると嬉しいです。これからも宜しくお願いします。"
     },
     fifth_button(){
      // 武将の名言
      this.TextAreaVal = "忠ならんと欲すれば孝ならず、孝ならんと欲すれば忠ならず"
     },
     sixth_button(){
      // 瀬戸内寂聴
      this.TextAreaVal = "一日に一回は鏡を見る方がいいです。できればにっこりと笑ってみてください。心にわだかまりがない時は、表情がいきいきしているはずですよ。"
     },
     seventh_button(){
       //  厚生労働省
      this.TextAreaVal = "これから三連休や夏休みで外出を予定されている方もいると思いますが、軽度の発熱、倦怠感など少しでも体調が悪ければ外出を控え、自治体等の方針に従って受診や検査をしましょう。"
     },
     eighth_button(){
       // みちょぱ　
      this.TextAreaVal = "ずっとやりたかった靴の衣替えがやっと終わった〜同時に冬物の履かなかった物たちの断捨離も！休みの日とかよりも仕事終わりの方が急に片付けスイッチ入るんだけど、これはあたしだけ？"
     },
     nineth_button(){
       // 松本人志
      this.TextAreaVal = "芸能人の巣ごもりでネタが無いのでしょう。ネットニュースは番組の感想文ばっかり。しかも変なキリトリだらけ…いやだ。いやだ。"
     },
     tenth_button(){
       // キング牧師
      this.TextAreaVal = "もし飛べないなら走ればいい。走れないのなら歩けばいい。歩けないのであれば、這っていけばいい。何があっても前に進み続けなければならなのです"
     },
        
        

    
      }
};
</script>
