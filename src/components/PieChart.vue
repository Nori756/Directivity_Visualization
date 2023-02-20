<script>
import { Pie } from "vue-chartjs";
import axios from 'axios'
export default {
  extends: Pie,
  mounted() {

    this.renderChart(
      {
        labels: ["男性", "女性"],
        datasets: [{
          backgroundColor: [
              "#4169e1",
              "#fa8072",
          ],
          data: [50, 50] //グラフのデータ
      }],
      },
     {
        responsive: true,
        maintainAspectRatio: false,
     //    title: {
     //      display: true,
    //       text: "Graph"
   //      },
         
      }
    );
    },

    methods: {

    roundup(value){
      const n = 3;
      return Math.round(value * Math.pow(10, n) ) / Math.pow(10, n);
    },
    minus_to_zero(value){
      if(value < 0){
        value = 0
      }
      return value
    },

    clearPieGraph(){

    this.renderChart(
      {
        labels: ["男性", "女性"],
        datasets: [{
          backgroundColor: [
              "#4169e1",
              "#fa8072",
          ],
          data: [50, 50] //グラフのデータ
      }],
      },
     {
        responsive: true,
        maintainAspectRatio: false,
     //    title: {
     //      display: true,
    //       text: "Graph"
   //      },
         
      }
    );
    },
      


    makePieGraph(values){
      let sum_M = this.minus_to_zero(values.M10) + this.minus_to_zero(values.M20) + this.minus_to_zero(values.M30) + this.minus_to_zero(values.M40) + this.minus_to_zero(values.M50) + this.minus_to_zero(values.M60)
      sum_M = this.roundup(sum_M)
      let sum_F = this.minus_to_zero(values.F10) + this.minus_to_zero(values.F20) + this.minus_to_zero(values.F30) + this.minus_to_zero(values.F40) + this.minus_to_zero(values.F50) + this.minus_to_zero(values.F60)
      sum_F = this.roundup(sum_F)

    
      // とりあえずの処理　足し合わせて、パーセント計算する

      if(sum_F == 0 && sum_M == 0){

        sum_F = 1
        sum_M = 1
      }


      // 全体数
      var max = sum_F + sum_M
      // AはBの何パーセントかを求める計算式
      var percent_M = sum_M / max * 100;
      var percent_F = sum_F / max * 100;

          
      this.renderChart(
      {
        labels: ["男性", "女性"],
        datasets: [{
          backgroundColor: [
              "#4169e1",
              "#fa8072",
          ],
          data: [percent_M, percent_F ] //グラフのデータ
      }],
          
          
      },
     {
        responsive: true,
        maintainAspectRatio: false,
     //    title: {
     //      display: true,
    //       text: "Graph"
   //      },
         
      }

    );
      }
  }
};
</script>
