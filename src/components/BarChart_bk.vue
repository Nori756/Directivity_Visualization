<script>
import { Bar } from "vue-chartjs";
import axios from 'axios'
export default {
  extends: Bar,
  mounted() {
     axios.get("https://jsonplaceholder.typicode.com/posts")
              .then((res) => {
                //console.log(res);
                var today = new Date()
                console.log(today)
                console.log("API通信成功")
                this.posts = res.data.posts;
              })
              .catch((err) => {
                console.log(err);
              }),
    
    this.renderChart(
      {
          labels: ["2022/2/1", "2022/2/2", "2022/2/3", "2022/2/4.", "2022/2/5", "2022/2/6", "2022/2/7", "2022/2/8", "2022/2/9", "2022/2/10", "2022/2/11", "2022/2/12"],
          datasets: [{
              label: "ワード1",
              borderWidth:1,
              backgroundColor: "#121554",
              borderColor: "#121554",
              data: [30000, 28000, 26000, 35000, 38000, 40000, 41000, 28000, 27000, 30000, 32000, 31000]
          },
           {
              label: "ワード2",
              borderWidth:1,
              backgroundColor: "#1d3681",
              borderColor: "#1d3681",
              data: [15000, 14000, 13000, 17500, 19000, 20000, 25000, 14000, 13500, 15000, 16000, 15500]
          },{
              label: "ワード3",
              borderWidth:1,
              backgroundColor: "#2e70a7",
              borderColor: "#2e70a7",
              data: [1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000,1000,1000]
          },{
              label: "ワード4",
              borderWidth:1,
              backgroundColor: "#4eadc7",
              borderColor: "#4eadc7",
              data: [1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000,1000,1000]
          },{
              label: "ワード5",
              borderWidth:1,
              backgroundColor: "#a7d8bf",
              borderColor: "#a7d8bf",
              data: [3000, 3000, 3000, 3000, 3000, 3000, 3000, 3000, 3000, 3000,3000,3000]
          }]

      },
     {
        responsive: true,
        maintainAspectRatio: false,
        title: {
          display: true,
          text: "Graph"
        },
         scales: {
              xAxes: [{
                    stacked: true, //積み上げ棒グラフにする設定
                    categoryPercentage:0.4 //棒グラフの太さ
              }],
              yAxes: [{
                    stacked: true //積み上げ棒グラフにする設定
              }]
          },
      }
    );
  }
};
</script>
