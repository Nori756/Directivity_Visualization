<script>
import { Bar } from "vue-chartjs";
import axios from 'axios'
export default {
  extends: Bar,
  mounted() {

    this.renderChart(
      {
          labels: ["10代", "20代", "30代", "40代.", "50代", "60代"],
          datasets: [
           {
              label: "男性",
              borderWidth:1,
              backgroundColor: "#4169e1",
              borderColor: "rgba(94,101,182,1)",
              data: [0,0,0,0,0,0]
          },
          {
              label: "女性",
              borderWidth:1,
              backgroundColor: "#fa8072",
              borderColor: "rgba(255,99,132,1)",
              data: [0,0,0,0,0,0]
          },        ]
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

    

    clearBarGraph(){

      this.renderChart(
      {
          labels: ["10代", "20代", "30代", "40代.", "50代", "60代"],
          datasets: [
           {
              label: "男性",
              borderWidth:1,
              backgroundColor: "#4169e1",
              borderColor: "rgba(94,101,182,1)",
              data: [0,0,0,0,0,0]
          },
          {
              label: "女性",
              borderWidth:1,
              backgroundColor: "#fa8072",
              borderColor: "rgba(255,99,132,1)",
              data: [0,0,0,0,0,0]
          },        ]
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


    makeBarGraph(values){

      this.renderChart(
      {
          labels: ["10代", "20代", "30代", "40代.", "50代", "60代"],
          datasets: [
           {
              label: "男性",
              borderWidth:1,
              backgroundColor: "#4169e1",
              borderColor: "rgba(94,101,182,1)",
              data: [values.M10 ,values.M20,values.M30,values.M40,values.M50,values.M60]
          },
          {
              label: "女性",
              borderWidth:1,
              backgroundColor: "#fa8072",
              borderColor: "rgba(255,99,132,1)",
              data: [values.F10 ,values.F20,values.F30,values.F40,values.F50,values.F60]
          },
          
          
          ]

      },
     {
        responsive: true,
        maintainAspectRatio: false,
        // title: {
       //    display: true,
       //    text: "棒グラフ"
      //   },
         
      }
    );
      }
  }
};
</script>
