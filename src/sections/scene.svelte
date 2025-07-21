<script>
// @ts-nocheck

    import Background from "../lib/Background.svelte";
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte"; 
    
    import ObservedText from "../lib/ObservedText.svelte";
    let chart;
    let chartOne;
    let show = $state(false);
    const chartOptions = {
        threshold: 0.0,
    };

    const callback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;
            if(entry.isIntersecting){
                show = true;
                // observer.unobserve(entry.target);
            }
           
        });
    };
    const period = 1000; // 1 second

    let optionsOne = {
        chart: {
            type: "column",
            backgroundColor: "#d49570",
            borderColor: "#ab481a",
            borderWidth: 8,
            borderRadius: 20,
            animation: true,
            marginTop: 80,
        },
        title: {
            text: "Nationwide attainment of Bachelor's Degrees",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                
            },
        },
        subtitle: {
            text: "From Black Wealth Data Center",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                
            },
        },
        yAxis:{
            title: {
                text: "% of Population with Bachelor's",
                style: {
                color: "#542e08",
                fontSize: "16px",
                fontFamily: "fantasy"
                }
            },
            labels: {
                style: {
                color: "#542e08",
                fontSize: "12px",
                fontWeight: 2000,
                fontFamily: "fantasy"
                }
            },
        },
        xAxis:{
            categories: ['Asian', 'Hispanic','Black','White'],
            labels: {
                style: {
                color: "#542e08",
                fontSize: "12px",
                fontWeight: 2000,
                fontFamily: "fantasy"
                }
            },
            gridLineColor: "#542e08",
            lineColor: "#542e08",
            lineWidth: 4,
            tickColor: "#542e08",
            tickWidth: 4,
        },
        legend:{
             itemStyle: {
                
                color: "#542e08",
                fontSize: "12px",
                fontWeight: 2000,
                fontFamily: "fantasy"
                
            },
        },
        plotOptions: {
            column:{
                borderWidth: 4,
                borderColor: "#542e08",
            },
            series: {
                animation:{
                    duration:1200
                },
                marker: {
                    enabled: false
                },
                lineWidth: 5
                
            } 
            
        },
        
        series:[
            {
                name: 'Men',
                data: [65.1, 19.6, 26.2, 41.0],
                color: "#FFDAC6"
            },
            {
                name:'Women',
                data: [60.8, 23.3, 31.4 , 43.6],
                color: "#7C6A0A"
            }
        ],
    };
   
   
    //chart two (series)
    let show1 = $state(false);
    
    const callback1 = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;
            if(entry.isIntersecting){
                show1 = true;
                // observer.unobserve(entry.target);
                
            }
           
        });
    };

    const seriesDataOne = [
    {
        type: "spline",
        name: "Asian",
        data: [[2011, 50.8],
                    [2012, 51.9],
                    [2013, 53.9],
                    [2014, 52.7],
                    [2015, 54.4],
                    [2016, 56.4],
                    [2017, 55.4],
                    [2018, 57.1],
                    [2019, 58.6],
                    [2020, 61.7],
                    [2021, 61.9],
                    [2022, 60.2],
                    [2023, 62.9]],
        color: "#7C6A0A",
        animation: { defer: 0 }
    },
    {
        type: "spline",
        name: "Hispanic",
        data: [[2011, 14.1],
                    [2012, 14.5],
                    [2013, 15.1],
                    [2014, 15.2],
                    [2015, 15.5],
                    [2016, 16.4],
                    [2017, 17.2],
                    [2018, 18.3],
                    [2019, 18.8],
                    [2020, 20.8],
                    [2021, 20.6],
                    [2022, 20.9],
                    [2023, 21.5]],
        color: "#c87a2b",
        animation: { defer: period }
    },
    {
        type: "spline",
        name: "Black",
        data: [[2011, 20.2],
                    [2012, 21.4],
                    [2013, 22.0],
                    [2014, 22.8],
                    [2015, 22.9],
                    [2016, 23.5],
                    [2017, 24.3],
                    [2018, 25.6],
                    [2019, 26.3],
                    [2020, 27.9],
                    [2021, 28.3],
                    [2022, 27.9],
                    [2023, 29.0]],
        color: "#ab481a",
        animation: { defer: period * 2 }
    },
    {
        type: "spline",
        name: "White",
        data: [[2011, 34.0],
                    [2012, 34.5],
                    [2013, 35.2],
                    [2014, 35.6],
                    [2015, 36.2],
                    [2016, 37.3],
                    [2017, 38.1],
                    [2018, 38.8],
                    [2019, 40.1],
                    [2020, 41.3],
                    [2021, 41.9],
                    [2022, 41.8],
                    [2023, 42.3]],
        color: "#98830c",
        animation: { defer: period * 3 }
    }
    ];

    let optionsTwo = {
        chart: {
            type: "spline",
            backgroundColor: "#BABD8D",
            borderColor: "#a8910e",
            borderWidth: 8,
            borderRadius: 20,
            animation: true,
        },
        title: {
            text: "Nationwide attainment of Bachelor's Degrees",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                
            },
        },
        subtitle: {
            text: "From Black Wealth Data Center",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                
            },
        },
        yAxis:{
            title: {
                text: "% of Population with Bachelor's",
                style: {
                color: "#542e08",
                fontSize: "16px",
                fontFamily: "fantasy"
                }
            },
            labels: {
                style: {
                color: "#542e08",
                fontSize: "12px",
                fontWeight: 2000,
                fontFamily: "fantasy"
                }
            },
            
        },
        xAxis:{
            labels: {
                style: {
                color: "#542e08",
                fontSize: "12px",
                fontWeight: 2000,
                fontFamily: "fantasy"
                }
            },
            gridLineColor: "#542e08",
            lineColor: "#542e08",
            lineWidth: 4,
            tickColor: "#542e08",
            tickWidth: 4,
        },
        legend:{
            itemStyle: {
                
                color: "#542e08",
                fontSize: "12px",
                fontWeight: 2000,
                fontFamily: "fantasy"
                
            },
        },
        gridLineColor: "#542e08",
        lineColor: "#542e08",
        lineWidth: 4,
        tickColor: "#542e08",
        tickWidth: 4,
        plotOptions: {
            series: {
                animation:{
                    duration:1200
                },
                marker: {
                    enabled: false
                },
                lineWidth: 5
                
            }
            
            
        },
        series: seriesDataOne,
    };
    //start by introducing how roi is measured
    //compare white man net worth to black man net worth -> then transition into black women to draw attention to the difference
    //put in context of STEM
    //compare degrees (in vs out in terms of money)
    //compare which races are likely to take on which degrees
    //look at how race effects education and job opportunity + income

    //chart Two
    
    
</script>

<div class="scene">
    <Background url="images/1.png" alignment={true}>
        <span class= "fancy1">What is a Bachelor's Degree Worth?</span>
    </Background>
    <Background url="images/2.png" alignment={true}>
        Today, women attain Bachelor's degrees at the <span class="fancy"> same rate or higher</span> than men of the same race
        <br><br> 
        <div class="chartOne">
            <ObservedText callback={callback} options={chartOptions}>
                {#if show}
                <Chart bind:chartOne options={optionsOne} highcharts={Highcharts}/>
                 {/if}
            </ObservedText>
        </div>
    </Background>
    <Background url="images/3.png" alignment={true}>
        And the percentage of minorities attaining Bachelor's degrees <span class="fancy"> increase </span> every year
        <br><br>     
        <div class="chart">
            <ObservedText callback={callback1} options={chartOptions}>
                {#if show1}
                <Chart bind:chart options={optionsTwo} highcharts={Highcharts}/>
                 {/if}
            </ObservedText>
        </div>
    </Background>
    <Background url="images/4.jpeg" alignment={true}>
        Therefore, the <span class="fancy"> Return on Investment (ROI) </span> should be comparable for graduates of <span class="fancy"> all </span>  backgrounds...
    </Background>
    <Background url="images/5.jpeg" alignment={true}>
        <span class="right">Right?</span>
    </Background>
    <Background url="images/6.jpeg" alignment={true}>
        <span class = "Right">Right?!</span>
    </Background>
</div>

<style>
    .scene{
        width: 100%;
        left: 0;
        height: auto;
        
    }
    .right{
        font-size: 7.5vw;
    }
    .Right{
        font-size: 12.5vw;
        padding-left: 5%;
        color: #ab481a;
        text-shadow: 5px 5px 0 #c87a2b;
        background-color: #FFDAC6;
    }
    .fancy{
        font-family:fantasy;
        color: #98830c;
        text-shadow: 2px 2px 0 #BABD8D;
        
    }
    .fancy1{
        font-size: 5.5vw;
        /* padding-left: 5%; */
        color: #df783d;
        font-family:fantasy;
        font-weight: 100;
        /* text-shadow: 5px 5px 0 #c87a2b; */
    }
    .chart{
        margin-left: 7vw;
        box-shadow: 0 2px 0px 5px #c87a2b;
        border-radius: 25px;
        z-index: 2;
        width: 80%;
        
    }
    .chartOne{
        margin-left: 3vw;
        /* box-shadow: 0 2px 0px 5px #c87a2b; */
        border-radius: 25px;
        z-index: 2;
        width: 80%;
    }
</style>