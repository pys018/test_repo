<template>

  <div>
    <highcharts class="hc" :options="chartOptions" ref="chart"></highcharts>
    
    </div>
      
  
  
</template>

<script>

export default {
computed: {
            computedCount(){
                console.log('computed');
                return this.countComputed;
            }
        },
  data() {
    
    return {
        
        
      
      chartOptions: {
        
  chart: {
          backgroundColor: '#323232',
          // backgroundColor: 'White',
          ignoreHiddenSeries: true,//serise 영역감추기
          spacingRight:122 ,//right 여백
          type: 'line' , //라인타입 종류  'spline' 
          zoomType: 'x', // x.y축 드래그줌인
    
  },
  legend: {
        floating: true,
        layout: 'vertical',
        borderWidth: 1,
        borderColor: '#444444',
        borderCornerRadius: 5,
        shadow: true,
        backgroundColor: 'rgba(32, 32, 32, .75)',
        align: 'left',
        x: 1300,
        verticalAlign: 'top',
        y: 30,
        itemStyle: {
            color: '#CCCCCC',
            listStyle: 'none',
            listStyleImage: 'none'
        },
        itemHiddenStyle: {
            color: '#444444'
        },
        itemHoverStyle: {
            color: 'white'
        }
    },
 plotOptions: {
      series: {
        marker: {
                enabled: false
            },
    }
  },
  
    yAxis: {
    lineWidth: 1,
    minorGridLineWidth: 0,
    minorTickInterval: 'auto',
    minorTickPosition: 'inside',
    minorTickWidth: 1
    
  },
  xAxis: {
    //  minRange: 5 ,//최대leng값 적용하기 힘들것같음..
    minTickInterval:5,
    lineWidth: 1,
    crosshair: {
            width: 2,
            color: 'gray'
            
        },
    type: 'datetime',
    plotLines: [{
            //현재시간 redline
            width: 1,
            color: '#FF0000',
            label: {
              style:{
                color:"#6F6F6F"
              },
              text: "+0 days, 20201114(1525)",//plot band 적용안됨
              y: 160
            },
            value: 30,
            
        },
        // {
        // color: "#494949",//그래프 시작선
        // width: 1,  
        // value: -0.5
        // },
        {
        color: "#494949",//그래프 끝선 
        width: 1,  
        value: 58
        },
        {
        color: "black",
        width: 1,
        label: {
          style:{
                color:"#6F6F6F"
              },
          text: "+1days 20201116",
          rotation: 90,
          align: "right",
          y: 315
        },
        value: 35
      },
      {
        color: "black",
        width: 1,
        label: {
          style:{
                color:"#6F6F6F"
              },
          text: "+2days 20201115",
          rotation: 90,
          align: "right",
          y: 315
          
        },
        value: 40
      },
      {
        color: "black",
        width: 1,
        label: {
          style:{
                color:"#6F6F6F"
              },
          text: "20201113",
          rotation: 90,
          align: "right",
          y: 315
        },
        value: 25
      },
      {
        color: "black",
        width: 1,
        label: {
          style:{
                color:"#6F6F6F"
              },
          color: "#5C5C5C",
          text: "20201112",
          rotation: 90,
          align: "right",
          y: 315
        },
        value: 20
      },
        ],
          // uniqueNames: true,// tooltip 상세 부제목 활성화
          categories: [-30	,-29	,-28	,-27	,-26	,-25	,-24	,-23	,-22	,-21	,-20	,-19	,-18	,-17	,-16	,-15	,-14	,-13	,-12	,-11	,-10	,-9	,-8	,-7	,-6	,-5	,-4	,-3	,-2	,-1	,0	,1	,2	,3	,4	,5	,6	,7	,8	,9	,10	,11	,12	,13	,14	,15	,16	,17	,18	,19	,20	,21	,22	,23	,24	,25	,26	,27	,28	,29	,30],//x축 title
          pointStart: Date.UTC(2020, 0, 1),
          pointInterval: 36e5,
          
          title:{
            x:5,
            textAlign:'left',
            width:10
          },
          
          tooltip: {
            
            xDateFormat: '%Y-%m-%d',//적용시 datatime 가져오지못함 
            crosshairs: true,
          shared: true,
          valueDecimals: 2,  
  },
          
  },
  //일반 x축 데이터 ( x-y둘다적용시 [ , ]) [[X,Y],[X,Y]]
        series: [
          {
        name:'20171211', 
        lineWidth: 4,
        data: [0.4299, 0.715, 0.21064, 0.11292, 0.01440, 0.01760, -1.01356,0.01440, 1.01760, -1.01356,2.1356, 0.01760,	2.21064	,0.01760	,-1.01356,0.1760,	3.11292,3.4299	,3.1292,0.01356,-2.01356,-0.4299	,0.3715,-1.01356,0.01440, 1.01760, -1.01356,2.1356, 0.01760,	2.21064	,0.01760	],
        color: 'red'
    },
    {
        name:'20181211', 
        lineWidth: 3,
        data: [-0.4299	,0.3715,	0.1292,	3.21064	,0.0760	,2.21064	,2.1760	,2.1356, 0.01760,	2.21064	,0.01760	,-1.01356,0.1760,	3.11292,3.4299	,3.1292,0.01356,-2.01356,-0.4299	,0.3715,	0.1292,	3.21064	,0.0760	,2.21064	,2.1760	,2.1356, 0.01760,	2.21064	,0.01760	,-1.01356,0.1760,	3.11292,3.4299	,3.1292,0.01356,-2.01356]
    },
    {
        name:'20191211', 
        lineWidth: 2,
        data: ['','',	'',-0.7485,	2.1760,	0.11292,3.4299	,-1.1292,	3.21064	,0.0760	,-2.01760	,0.1356,3.3715,	0.1129,0.1356,-3.3715,	0.11292,	4.21064	,3.1760	,-1.01356,-1.1292,	3.21064	,0.0760	,-2.01760	,0.1356,3.3715,	0.1129,0.1356,-3.3715,	0.11292,	4.21064	,3.1760	,-1.01356,-1.1292,	3.21064	,0.0760	,-2.01760	,0.1356,3.3715,	0.1129,0.1356,-3.3715,	0.11292,	4.21064	,3.1760	,-1.01356,-1.1292,	3.21064	,0.0760	,-2.01760	,0.1356,3.3715,	0.1129,0.1356,-3.3715,	0.11292,	4.21064	,3.1760	,-1.01356],
        color: 'blue'

    },
      
    {  
        name:'20201211', 
        lineWidth: 1,
        data: [-0.1760	,0.1356,0.3715,	1.11292,	0.21064	,0.1760	,1.1356,0.1760,	0.11292,3.4299	,3.1292,	3.21064	,0.0760	,0.01760	,0.1356,0.3715,	0.11292,	0.21064	,0.1760	,0.01356],
        color:'orange'
    }
    ],
    
      }
    };
  }
  };
  </script>
