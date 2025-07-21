<script>
// @ts-nocheck

    import Background from "../lib/Background.svelte";
    import ObservedText from "../lib/ObservedText.svelte";
    import { Chart } from '@highcharts/svelte';
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import ArticleText from "../lib/ArticleText.svelte";
    import {fade} from 'svelte/transition';
    // svelte-ignore non_reactive_update
    const chartOptions = {
        threshold: 0.0,
    };
        
    // let chartOne;
    let chart;
    let show = $state(false);
    

    const callback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;
            if(entry.isIntersecting){
                show = true;
                console.log("true");
                // observer.unobserve(entry.target);
            }else{
                show = false;
                console.log("falseeee");
            }
           
        });
    };
    const period = 1000; // 1 second

    let optionsOne = {
        chart: {
            type: "column",
            backgroundColor: "#d49570",
            borderColor: "#c87a2b",
            borderWidth: 8,
            borderRadius: 20,
            animation: true,
            spaceTop: "30",
        },
        title: {
            text: "Percentage of Bachelor's Degree Recipients Majoring in STEM (from ClevelandFed.org)",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                fontSize:"25px"
            },
        },
        // subtitle: {
        //     text: "From Black Wealth Data Center",
        //     style: {
        //         color:"#542e08",
        //         fontFamily: "fantasy",
                
        //     },
        // },
        yAxis:{
            title: {
                text: "% of Population",
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
                fontWeight: "2000",
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
                fontWeight: "2000",
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
                fontWeight: "2000",
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
                data: [32, 14, 11, 16],
                color: "#98830c"
            },
        ],
    };

    let chartTwo;
    let show2 = $state(false);
    

    const callbackTwo = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;
            if(entry.isIntersecting){
                show2 = true;
                // observer.unobserve(entry.target);
            }
           
        });
    };
    

    let optionsTwo = {
        chart: {
            type: "column",
            backgroundColor: "#d49570",
            borderColor: "#c87a2b",
            borderWidth: 8,
            borderRadius: 20,
            animation: true,
            spaceTop: "30",

        },
        title: {
            text: "Percentage of Bachelor's Degree Recipients Majoring in Area, Ethnic, Cultural, Gender, and Group Studies Subjects (ClevelandFed.org)",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                fontSize:"25px"
                
            },
        },
        // subtitle: {
        //     text: "From ClevelandFed.org",
        //     style: {
        //         color:"#542e08",
        //         fontFamily: "fantasy",
        //         fontSize:"15px",
        //         paddingTop: "20px"
                
        //     },
        // },
        yAxis:{
            title: {
                text: "% of Population",
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
                fontWeight: "2000",
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
                fontWeight: "2000",
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
                fontWeight: "2000",
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
                data: [1, 1.1, 0.78, 0.45],
                color: "#c87a2b"
            },
            
        ],
    };

    let chartThree;
    let show3 = $state(false);
    

    const callbackThree = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;
            if(entry.isIntersecting){
                show3 = true;
                // observer.unobserve(entry.target);
            }
           
        });
    };
   

    let optionsThree = {
        chart: {
            type: "column",
            backgroundColor: "#d49570",
            borderColor: "#c87a2b",
            borderWidth: 8,
            borderRadius: 20,
            animation: true,
            spaceTop: "30",
        },
        title: {
            text: "Percentage of Bachelor's Degree Recipients Majoring in Public Administration and Social Service Professions Subjects (ClevelandFed.org)",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                fontSize:"25px"
            },
        },
        // subtitle: {
        //     text: "From Black Wealth Data Center",
        //     style: {
        //         color:"#542e08",
        //         fontFamily: "fantasy",
                
        //     },
        // },
        yAxis:{
            title: {
                text: "% of Population",
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
                fontWeight: "2000",
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
                fontWeight: "2000",
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
                fontWeight: "2000",
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
                data: [0.7, 2.5, 4, 1.5],
                color: "#ab481a"
            },
           
        ],
    };
</script>

    <Background >
        <div class="wrapper" >
        <div class="scroll">
            <ObservedText callback={callback} options={chartOptions}>
                Let's take a look at racial composition based on major choice...
            </ObservedText>
        </div>
        <!-- {#if show} -->
        <div class="chartRow" in:fade={{ duration: 800}} out:fade={{duration: 800}} style={`opacity: ${show? "1":"0"}`}>
            <div class="chartWrapper">
                <div class="chart"><Chart bind:chart options={optionsOne} highcharts={Highcharts}/></div>
                <div class="chart"><Chart bind:chartTwo options={optionsTwo} highcharts={Highcharts}/></div>
                <div class="chart"><Chart bind:chartThree options={optionsThree} highcharts={Highcharts}/></div>
                <!-- <ArticleText>trackinggg</ArticleText> -->
            </div>
        </div>
        <!-- {/if} -->
    </div>
    </Background>
    
    


<style>
    
     .chart{
        width: 30%;
        aspect-ratio: 1/1;
        height: auto;
     }
    .wrapper {
        width: 100%;
        min-height: 100vh;
        position: relative;
        z-index: 1;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .scroll {
        z-index: 2;
        width: 100%;
        min-height: 30vh;
        position: relative;
        display: flex;
        align-items: center;
        text-align: center;
        background: transparent;
        font-size: 1.5rem;
        font-weight: bold;
        background-color:#ffdac6d1;
        
    }

    .chartRow {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: auto;
        display: flex;
        aspect-ratio: 2/1;
        align-items: center;
        justify-content: center;
        z-index: 0;
        padding: 0;
        transition: opacity 2000ms ease;
        pointer-events: none; /* Allow text to scroll over it */
    }

    .chartWrapper {
        display: flex;
        width: 100%;
        max-width: 1400px;
        height: auto;
        justify-content: space-between;
        align-items: center;
        pointer-events: auto;
        /* box-shadow: 0 0 0 8px #c87a2b;
        border-radius: 25px; */
        
    }

</style>