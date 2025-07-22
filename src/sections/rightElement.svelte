<script>
// @ts-nocheck

    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import ObservedText from "../lib/ObservedText.svelte";

    let chart;
    // let chartOne;
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
            borderColor: "#c87a2b",
            borderWidth: 8,
            borderRadius: 20,
            animation: true,
            marginTop: 80,
        },
        title: {
            text: "Percentage Employment in STEM Roles (2021)",
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
                text: "% of Bachelor's Degree Grads Employed in STEM",
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
                data: [55.5, 36.4, 31.1 , 40],
                color: "#98830c"
            }
        ],
    };

</script>

<div>
    <Scroller layout="right" keepSticky={true}>
        {#snippet sticky()}
            <div class="chartOne">
                <ObservedText callback={callback} options={chartOptions}>
                    {#if show}
                        <Chart bind:chart options={optionsOne} highcharts={Highcharts}/>
                    {/if}
                </ObservedText>
            </div>
        {/snippet}

        {#snippet scrolly()}
        <div class="text">
            <h1 class="description"><span class="fancy">Race Employment Disparity in STEM</span> <br>for those with STEM Bachelor's Degrees <br> (Data from BWDC)</h1>
        </div>
            
        {/snippet}
    </Scroller>
</div>

<style>
    div{
        margin: 0;
        position: relative;
        z-index: 2;
        text-align: center;
        background-color: #FFDAC6;
        width: 100%;
        height: auto;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
     h1{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        padding: 0;
        margin: 0;
        font-size: 5vw;
        color: #df783d;
        font-family: fantasy;
        
    }
    .chartOne{
        width: 80%;
        position: fixed;
    }
    .fancy{
        font-size: 3vw;
        font-family:fantasy;
        color: #98830c;
        text-shadow: 2px 2px 0 #BABD8D;
        
    
    }
    .text{
        /* background-color: #b7a01a; */
        right: 5%;
        width: 100%;
        
    }
    .description{
        display: block;
        text-align: center;
        font-size: 2.5vw;
    }
   @media (max-width: 768px){
        .chartOne{
            position: relative;
        }
        .text{
            right: 0;
        }
        .counter-label{
            font-size: 3.5vw;
        }
        .description{
            width: 80%;
            padding-top: 55px;
            padding-bottom: 25px;
            font-size: 3.5vw;
            left:0;
        }
        .fancy{
            font-size: 4.5vw;
        }
    }
   
</style>