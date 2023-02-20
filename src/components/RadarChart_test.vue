<script>
import { Radar } from "vue-chartjs";

export default {
  extends: Radar,
  mounted() {
    this.renderChart(
        {
          labels: [
            "10代",
            "20代",
            "30代",
            "40代",
            "50代",
            "60代",
          
          ],
          datasets: [
            {
              label: "男性",
              backgroundColor: "rgba(94,101,182,0.2)",
              borderColor: "rgba(94,101,182,1)",
              pointBackgroundColor: "rgba(94,101,182,1)",
              pointBorderColor: "#fff",
              pointStyle: "triangle",     // 点のスタイル 三角
              pointRadius: 5,
              pointHoverBackgroundColor: "#fff",
              pointHoverBorderColor: "rgba(94,101,182,1)",
            },
            {
              label: "女性",
              backgroundColor: "rgba(255,99,132,0.2)",
              borderColor: "rgba(255,99,132,1)",
              pointBackgroundColor: "rgba(255,99,132,1)",
              pointBorderColor: "#fff",
              pointHoverBackgroundColor: "#fff",
              pointHoverBorderColor: "rgba(255,99,132,1)",
            }
          ]
        },
        { responsive: true, maintainAspectRatio: false,

        legend: {              // 凡例の表示位置
              labels: {              // 凡例の表示内容
            fontSize: 12,           // 文字のサイズ
            boxWidth: 12,           // 点のサイズ
            usePointStyle: true     // 凡例図形を点にする
        }}
        
        }
      )
  },
  methods: {

    sendAPI(formtext){
              
        this.renderChart(
          {
            labels: [
             "10代",
            "20代",
            "30代",
            "40代",
            "50代",
            "60代",
            
            ],
            datasets: [
              {
                label: "Male",
                backgroundColor: "rgba(94,101,182,0.2)",
                borderColor: "rgba(94,101,182,1)",
                pointBackgroundColor: "rgba(94,101,182,1)",
                pointBorderColor: "#fff",
                pointStyle: "triangle",     // 点のスタイル 三角
                pointRadius: 5,
                pointHoverBackgroundColor: "#fff",
                pointHoverBorderColor: "rgba(94,101,182,1)",
                data: [5, 5, 5, 4, 4, 5]

              },
              {
                label: "Female",
                backgroundColor: "rgba(255,99,132,0.2)",
                borderColor: "rgba(255,99,132,1)",
                pointBackgroundColor: "rgba(255,99,132,1)",
                pointBorderColor: "#fff",
                pointHoverBackgroundColor: "#fff",
                pointHoverBorderColor: "rgba(255,99,132,1)",
                data: [1, 2, 3, 4, 1, 1]
              }
            ]
          },
          { responsive: true, maintainAspectRatio: false,
              legend: {              // 凡例の表示位置
              labels: {              // 凡例の表示内容
            fontSize: 12,           // 文字のサイズ
            boxWidth: 12,           // 点のサイズ
            usePointStyle: true     // 凡例図形を点にする
        }}
          
           }
        )
    }
      }
              
  };
</script>