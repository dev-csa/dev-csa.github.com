---
layout: post
title: "자바스크립트 Chart 라이브러리 추천"
excerpt: Javascript Library 
categories: [hello world]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---


# 자바스크립트로 Chart 그리는 작업 시 유용한 라이브러리

[ECharts]  https://ecomfe.github.io/echarts-examples/public/index.html

<img src="https://cdn-images-1.medium.com/max/800/1*Q7dFNsCP0eSi23quzWs1fQ.jpeg">


<br/><br/>
eChart는 상당히 많은 종류의 차트를 제공하고있으며, 그래프와 함께 기본적으로 제공되는 쓸만한 기능들이 많다. 

한가지 단점이라면, 중국어로 되어 있다는 점인데, 어차피 소스코드는 영어이므로 문제없이 이용가능


 <h4> - Line and Bar mix chart 이용한 예시 
 <br/>
 
    <h5>1월~5월의 오전-오후 기온과 평균습도 그래프 
 
 
     ```
     
    <script type="text/javascript">
            var dom = document.getElementById("container");
            var myChart = echarts.init(dom, 'blue');
            var app = {};
            var morning_data = [2.0, 4.9, 7.0, 23.2, 25.6];
            var evening_data = [2.6, 5.9, 9.0, 26.4, 28.7];
            var Humidity = [55, 43, 87, 22, 76];
    
            option = null;
            app.title = 'Line and bar';
    
            option = {
                tooltip: {
                    trigger: 'axis',
                    axisPointer: {
                        type: 'cross'
                    }
                },
                toolbox: {
                    feature: {
                        dataView: {show: true, readOnly: false},
                        magicType: {show: true, type: ['line', 'bar']},
                        restore: {show: true},
                        saveAsImage: {show: true}
                    }
                },
                legend: {
                    data:['오전','오후','습도']
                },
                xAxis: [
                    {
                        type: 'category',
                        data: ['1月','2月','3月','4月','5月'],
                        axisPointer: {
                            type: 'shadow'
                        }
                    }
                ],
                yAxis: [
                    {
                        type: 'value',
                        name: 'r1',
                        min: 0,
                        max: 100,
                        interval: 5,
                        axisLabel: {
                            formatter: '{value}'
                        }
                    },
                    {
                        type: 'value',
                        name: '',
                        min: 0,
                        max: 100,
                        interval: 5,
                        axisLabel: {
                            formatter: '{value}'
                        }
                    }
                ],
                series: [
                    {
                        name:'오전',
                        type:'bar',
                        label: {
                            normal: {
                                show: true,
                                position: 'top'
                            }
                        },
                        data: morning_data
                        
                    },
                    {
                        name:'오후',
                        type:'bar',
                        label: {
                            normal: {
                                show: true,
                                position: 'top'
                            }
                        },
                        data: evening_data
                    },
                    {
                        name:'습도',
                        type:'line',
                        label: {
                            normal: {
                                show: true,
                                position: 'inside'
                            }
                        },
                        yAxisIndex: 1,
                        data: Humidity
                    }
                ]
            };
            ;
            if (option && typeof option === "object") {
                myChart.setOption(option, true);
            }
    </script>
    ```

<img src="https://cdn-images-1.medium.com/max/800/1*JYUthLv6XEIEKUX6UaVVZA.jpeg"> 

<br/><br/><br/>

toolbox 항목에서 그래프를 사용자가 만질 수 있도록 하는 기능을 추가할 수 있는데, 

이 기능이 제일 맘에 들지만 한자로 나온다는게 문제! 

영문으로 바꾸는 방법을 찾는다면 추후 기재 하도록 하겠음.
