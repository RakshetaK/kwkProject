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
                // if(window.innerWidth<=768){
                //     var element = document.getElementById("one");
                //     element.text = "In addition to systemic barriers causing imbalances in employment (as shown for STEM professions), Choice of major also plays a significant role in the benefits (a.k.a return on investment) of a bachelor's degree. So how do this data correspond to racial disparities in ROI?"
                // }
                // observer.unobserve(entry.target);
            }else{
                show = false;
            }
           
        });
    };
    const period = 1000; // 1 second

    let optionsOne = {
        chart: {
            type: "bar",
            backgroundColor: "#BABD8D",
            borderColor: "#a8910e",
            borderWidth: 8,
            borderRadius: 20,
            animation: true,
            marginTop: 80,
        },
        title: {
            text: "Projected ROI by Major (as of 2023)",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                fontSize: "25px",
                
            },
        },
        subtitle: {
            text: "From EducationData.org",
            style: {
                color:"#542e08",
                fontFamily: "fantasy",
                
            },
        },
        yAxis:{
            title: {
                text:"ROI in 10 years(%)",
                style: {
                color: "#542e08",
                fontSize: "20px",
                fontFamily: "fantasy",
                textAlign: "center",
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
            gridLineColor: "#542e08",
            lineColor: "#542e08",
            lineWidth: 4,
            tickColor: "#542e08",
            tickWidth: 4,
        },
        xAxis:{
            categories: ['Computer Engineering', 'Electrical Engineering','Health','Transportation', 'Mathematics','Social Sciences','International Relations','Linguistics','Public Administration','Social Services'],
            
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
            bar:{
                borderWidth: 4,
                pointWidth: 20,
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
                data: [126.15,98.11,-7,40.18,51.31,28.39,48.57,-69.78,28.39,-66.61],
                color: "#ab481a"
            }
        ],
    };
</script>

    <Background >
         <div class="wrapper" >
            <div class="scroll"id="two" >
            <ObservedText callback={callback} options={chartOptions}>
                In addition to systemic barriers causing imbalances in employment (as shown for STEM professions)...
            </ObservedText>
            
        </div>
       
        <!-- {#if show} -->
        <div class="chartRow" in:fade={{duration:800}} out:fade={{ duration: 1000}} style={`opacity: ${show? "1":"0"}`}>
            <div class="chartWrapper">
                <Chart bind:chart options={optionsOne} highcharts={Highcharts}/>
            </div>
        </div>
        <!-- {/if} -->
          
        <div class="scroll" id="one">
            <ObservedText callback={callback} options={chartOptions}>
                Choice of major also plays a significant role in the benefits (a.k.a return on investment) of a bachelor's degree
            </ObservedText>
        </div>
        <div class="scroll" id="three">
            <ObservedText callback={callback} options={chartOptions}>
                So how do this data correspond to racial disparities in ROI?
            </ObservedText>
        </div>
    </div>
    </Background>
   
    


<style>
    .wrapper{
        width: 100%;
        min-height: 100vh;
        /* min-height: 100vh; */
        /* background-color: #FFDAC6; */
        left: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        
    }
    .chartRow{
        position:fixed;
        display: flex;
        align-items: center;
        justify-content: center;
        left: 0;
        width: 100%;
        height: 100%;
        top: 50vh;
        transition: opacity 2000ms ease;
        transform: translateY(-50%);
        z-index: 0;
        
    }
    .chartWrapper {
        width: 95%; /* adjust as needed */
        max-width: 1400px;
        height: auto;
        pointer-events: auto; /* Ensure interaction if needed */
        box-shadow: 0 0 0 8px #c87a2b;
        border-radius: 25px;
        
    }
    .scroll{
        position: relative;
        z-index: 1;
        display: flex;
        align-items: center;
        min-height: 30vh;
        width: 100%;
        background-color: #ffdac6d1;
        margin-top: 50vh;
        margin-bottom: 50vh;
        
    }
   
</style>