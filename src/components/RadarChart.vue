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
        { responsive: true, maintainAspectRatio: false ,
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

    roundup(value) {
      const n = 3;
      return Math.round(value * Math.pow(10, n) ) / Math.pow(10, n);
    },

     clearRaderGraph(){
      //グラフ初期化関数

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
        { responsive: true, maintainAspectRatio: false ,
         legend: {              // 凡例の表示位置
              labels: {              // 凡例の表示内容
            fontSize: 12,           // 文字のサイズ
            boxWidth: 12,           // 点のサイズ
            usePointStyle: true     // 凡例図形を点にする
        }}
        
        }
      )
      },

    sendAPI(formtext){
      var directivity;
    
      this.axios.post('https://aoi.naist.jp/transmission/transmit/?text=' + formtext)
      .then((response) => {
                //console.log(response.data);
                //console.log({F10:response.data.F10[0], M10:response.data.F20[0]});
          this.$parent.directivity_data = [{
            F10:this.roundup(response.data.F10[0]), F20:this.roundup(response.data.F20[0]),
            F30:this.roundup(response.data.F30[0]), F40:this.roundup(response.data.F40[0]),
            F50:this.roundup(response.data.F50[0]), F60:this.roundup(response.data.F60[0]),
            M10:this.roundup(response.data.M10[0]), M20:this.roundup(response.data.M20[0]),
            M30:this.roundup(response.data.M30[0]), M40:this.roundup(response.data.M40[0]),
            M50:this.roundup(response.data.M50[0]), M60:this.roundup(response.data.M60[0]),
          
          }];
        

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
                data: [response.data.M10[0], response.data.M20[0], response.data.M30[0], 
                      response.data.M40[0], response.data.M50[0], response.data.M60[0]]
               
              },
              {
                label: "女性",
                backgroundColor: "rgba(255,99,132,0.2)",
                borderColor: "rgba(255,99,132,1)",
                pointBackgroundColor: "rgba(255,99,132,1)",
                pointBorderColor: "#fff",
                pointHoverBackgroundColor: "#fff",
                pointHoverBorderColor: "rgba(255,99,132,1)",
                data: [response.data.F10[0], response.data.F20[0], response.data.F30[0], 
                       response.data.F40[0], response.data.F50[0], response.data.F60[0]]
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
              })
              .catch((err) => {
                console.log(err);
              });
      },
      
      },

   
      
              
  };
</script>