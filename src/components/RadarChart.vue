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
        { responsive: true, maintainAspectRatio: false }
      )
  },
  methods: {

    sendAPI(formtext){
    
      this.axios.post('https://aoi.naist.jp/transmission/transmit/?text=' + formtext, 
              ).then(response => 
              
              
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
          { responsive: true, maintainAspectRatio: false }
        )
      
      )
                .catch(error => console.log(error))
      }
      }
              
  };
</script>