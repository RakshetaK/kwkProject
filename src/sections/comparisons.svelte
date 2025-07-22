<script>
// @ts-nocheck

    import Background from "../lib/Background.svelte";
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte"; 
    import Counter from "../lib/counter.svelte";
    import ObservedText from "../lib/ObservedText.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import Scroller from "../lib/Scroller.svelte";
    import RaceByMajor from "./raceByMajor.svelte";
    import {fade} from "svelte/transition";
    import LeftElement from "./leftElement.svelte";
    import RightElement from "./rightElement.svelte";
    import RoiByMajor from "./roiByMajor.svelte";
    //add a countUp callback function when text is 100% in screen
    
   
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
   
   
    // //chart two (series)
    // let show1 = $state(false);
    
    // const callback1 = (entries, observer) => {
    //     entries.forEach((entry) => {
    //         const elem = entry.target;
    //         if(entry.isIntersecting){
    //             show1 = true;
    //             // observer.unobserve(entry.target);
                
    //         }
           
    //     });
    // };

    // const seriesDataOne = [
    // {
    //     type: "spline",
    //     name: "Asian",
    //     data: [[2011, 50.8],
    //                 [2012, 51.9],
    //                 [2013, 53.9],
    //                 [2014, 52.7],
    //                 [2015, 54.4],
    //                 [2016, 56.4],
    //                 [2017, 55.4],
    //                 [2018, 57.1],
    //                 [2019, 58.6],
    //                 [2020, 61.7],
    //                 [2021, 61.9],
    //                 [2022, 60.2],
    //                 [2023, 62.9]],
    //     color: "#7C6A0A",
    //     animation: { defer: 0 }
    // },
    // {
    //     type: "spline",
    //     name: "Hispanic",
    //     data: [[2011, 14.1],
    //                 [2012, 14.5],
    //                 [2013, 15.1],
    //                 [2014, 15.2],
    //                 [2015, 15.5],
    //                 [2016, 16.4],
    //                 [2017, 17.2],
    //                 [2018, 18.3],
    //                 [2019, 18.8],
    //                 [2020, 20.8],
    //                 [2021, 20.6],
    //                 [2022, 20.9],
    //                 [2023, 21.5]],
    //     color: "#c87a2b",
    //     animation: { defer: period }
    // },
    // {
    //     type: "spline",
    //     name: "Black",
    //     data: [[2011, 20.2],
    //                 [2012, 21.4],
    //                 [2013, 22.0],
    //                 [2014, 22.8],
    //                 [2015, 22.9],
    //                 [2016, 23.5],
    //                 [2017, 24.3],
    //                 [2018, 25.6],
    //                 [2019, 26.3],
    //                 [2020, 27.9],
    //                 [2021, 28.3],
    //                 [2022, 27.9],
    //                 [2023, 29.0]],
    //     color: "#ab481a",
    //     animation: { defer: period * 2 }
    // },
    // {
    //     type: "spline",
    //     name: "White",
    //     data: [[2011, 34.0],
    //                 [2012, 34.5],
    //                 [2013, 35.2],
    //                 [2014, 35.6],
    //                 [2015, 36.2],
    //                 [2016, 37.3],
    //                 [2017, 38.1],
    //                 [2018, 38.8],
    //                 [2019, 40.1],
    //                 [2020, 41.3],
    //                 [2021, 41.9],
    //                 [2022, 41.8],
    //                 [2023, 42.3]],
    //     color: "#98830c",
    //     animation: { defer: period * 3 }
    // }
    // ];

    // let optionsTwo = {
    //     chart: {
    //         type: "spline",
    //         backgroundColor: "#BABD8D",
    //         borderColor: "#a8910e",
    //         borderWidth: 8,
    //         borderRadius: 20,
    //         animation: true,
    //     },
    //     title: {
    //         text: "Nationwide attainment of Bachelor's Degrees",
    //         style: {
    //             color:"#542e08",
    //             fontFamily: "fantasy",
                
    //         },
    //     },
    //     subtitle: {
    //         text: "From Black Wealth Data Center",
    //         style: {
    //             color:"#542e08",
    //             fontFamily: "fantasy",
                
    //         },
    //     },
    //     yAxis:{
    //         title: {
    //             text: "% of Population with Bachelor's",
    //             style: {
    //             color: "#542e08",
    //             fontSize: "16px",
    //             fontFamily: "fantasy"
    //             }
    //         },
    //         labels: {
    //             style: {
    //             color: "#542e08",
    //             fontSize: "12px",
    //             fontWeight: 2000,
    //             fontFamily: "fantasy"
    //             }
    //         },
            
    //     },
    //     xAxis:{
    //         labels: {
    //             style: {
    //             color: "#542e08",
    //             fontSize: "12px",
    //             fontWeight: 2000,
    //             fontFamily: "fantasy"
    //             }
    //         },
    //         gridLineColor: "#542e08",
    //         lineColor: "#542e08",
    //         lineWidth: 4,
    //         tickColor: "#542e08",
    //         tickWidth: 4,
    //     },
    //     legend:{
    //         itemStyle: {
                
    //             color: "#542e08",
    //             fontSize: "12px",
    //             fontWeight: 2000,
    //             fontFamily: "fantasy"
                
    //         },
    //     },
    //     gridLineColor: "#542e08",
    //     lineColor: "#542e08",
    //     lineWidth: 4,
    //     tickColor: "#542e08",
    //     tickWidth: 4,
    //     plotOptions: {
    //         series: {
    //             animation:{
    //                 duration:1200
    //             },
    //             marker: {
    //                 enabled: false
    //             },
    //             lineWidth: 5
                
    //         }
            
            
    //     },
    //     series: seriesDataOne,
    // };
    //start by introducing how roi is measured
    //compare white man net worth to black man net worth -> then transition into black women to draw attention to the difference
    //put in context of STEM
    //compare degrees (in vs out in terms of money)
    //compare which races are likely to take on which degrees
    //look at how race effects education and job opportunity + income

    //chart Two
    
    
</script>

<div class="scene">
    <div class="ROI">
        <h1>What indicates good ROI?</h1>
        <ArticleText> A <span class="fancy">Return on Investment</span> is a metric used to weigh the <span class="fancy">profit vs cost</span> of an investment. In the case of a bachelor's degree, that would be the <span class="fancy">cost of tuition</span> and a factor that involves either <span class="fancy">net worth</span> or <span class="fancy">entry salary</span> for that major.</ArticleText>
        <div class= "equation" style={`background-image: url('images/9.PNG'); background-size: cover;`}></div>
    </div>
     
    
    
    <Background url="images/7.PNG" alignment={false}>
       <h1 class="title">ROI from a Bachelor's Degree (Black Man vs. White Man)</h1>
         <span class="sub">(Data from educationdata.org and BWDC) *Does not account for scholarships, loans, or major.</span>
         <br><br><br>
        <div class = 'column-wrapper'>
            <div class="black-man">
                <h1 class="label">$<Counter value={298}/>K</h1>
                <span class="counter-label">Net Worth</span>
                
                <h1 class="label">$<Counter value={109}/>K</h1>
                <span class="counter-label">Average College Tuition <span class="sub">(public, on campus, in-state)</span></span>
                
                <h1 class="label"><Counter value={173}/>%</h1>
                <span class="counter-label">Return on Investment</span>
            </div>
            <div class="white-man">
                <h1 class="label">$<Counter value={748}/>K</h1>
                <span class="counter-label">Net Worth</span>
                
                <h1 class="label">$<Counter value={109}/>K</h1>
                <span class="counter-label">Average College Tuition <br><span class="sub">(public, on campus, in-state)</span></span>
                
                <h1 class="label"><Counter value={586}/>%</h1>
                <span class="counter-label">Return on Investment</span>
            </div>
        </div>
        
    </Background>
    <Background url="images/8.PNG" alignment={false}>
        <h1 class="title">ROI from a Bachelor's Degree (Black Woman vs. White Man)</h1>
        <span class="sub">(Data from <a href="https://educationdata.org/average-cost-of-college">educationdata.org</a> and BWDC) *Does not account for scholarships, loans, or major.</span>
        <br><br><br>
        <div class = 'column-wrapper'>
            <div class="black-woman">
                <h1 class="label">$<Counter value={89}/>K</h1>
                <span class="counter-label">Net Worth</span>
                
                <h1 class="label">$109K</h1>
                <span class="counter-label">Average College Tuition <span class="sub">(public, on campus, in-state)</span></span>
                
                <h1 class="label">-<Counter value={18}/>%</h1>
                <span class="counter-label">Return on Investment</span>
            </div>
            <div class="white-man">
                <h1 class="label">$748K</h1>
                <span class="counter-label">Net Worth</span>
                
                <h1 class="label">$109K</h1>
                <span class="counter-label">Average College Tuition <span class="sub">(public, on campus, in-state)</span></span>
                
                <h1 class="label">586%</h1>
                <span class="counter-label">Return on Investment</span>
            </div>
        </div>
        
    </Background>
    
   
    <LeftElement />
    <RightElement />
    <RoiByMajor />
    <RaceByMajor />
    <div class="ROI-conclusion">
        <h1>Based on the data...</h1>
        <ArticleText>  It is evident that there exist <span class="fancy">systemic barriers</span> that prevent a beneficial relationship between the <span class="fancy">cost</span> and <span class="fancy">return</span> of a degree.
            <br><br> 
            Race-based data on major selection shows that many <span class="fancy">minority </span> students tend to choose majors with low ROI, a decision that can largely be attributed to <span class="fancy"> information gaps.</span>
        </ArticleText>
        <div class= "scale" style={`background-image: url('images/10.PNG'); background-size: cover;`}></div>
        <ArticleText>
        Many of these students, being <span class="fancy"> first generation graduates, </span> bear significant financial responsibilities that impede recovery from a low ROI and impact their <span class="fancy"> wealth accumulation.</span>
        </ArticleText>
    </div>
    <br><br><br><br><br><br>
    <div class="info-gap" id = "info-gap">
            <h1>How can information gaps be closed?</h1>
            <div class="marquee-wrapper">
                <div class="marquee">
                    <img src="images/11.PNG" alt=""> 
                    <img src="images/12.PNG" alt="">
                    <img src="images/13.PNG" alt="">
                    <img src="images/11.PNG" alt=""> 
                    <img src="images/12.PNG" alt="">
                    <img src="images/13.PNG" alt="">
                    <img src="images/11.PNG" alt=""> 
                    <img src="images/12.PNG" alt="">
                    <img src="images/13.PNG" alt="">
                    
                </div>
            </div>
        </div>
        <Background url='images/1.png' alignment={true}>
            <h1>
                <span class="end"> With the removal of DEI initiatives, <span class="fancy2">it is critical</span> that we step up. 
                <br><br>
                Students from all backgrounds deserve the access <span class="fancy2"> to ROI data, career guidance, and opportunities </span>  that enable them to assign worth to their Bachelor's Degree.</span>
            </h1>

        </Background>
        
    <!-- <ArticleText>Race Employment Disparity in STEM <br> <span class="sub"> for those with STEM Bachelor's Degrees</span></ArticleText>
    <ArticleText>BreakDown of Majors that yield highest ROI <br> <span class="sub">https://educationdata.org/college-degree-roi</span></ArticleText>
    <ArticleText>BreakDown of races that take on each major <br> <span class="sub">https://www.clevelandfed.org/publications/economic-trends/2015/et-20150331-racial-and-ethnic-differences-in-college-major-choice</span></ArticleText>
    <ArticleText>Passion vs Practicality: Does ROI Always Win?</ArticleText>
    <ArticleText>What does the future of ROI for Bachelor's degrees look like under our current administration?</ArticleText> -->

    
</div>

<style>
    .ROI{
        background-color: #FFDAC6;
        width: 100%;
        height: auto;
        z-index: 2;
        position: relative;
        /* padding-top: 3%; */
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }
    a{
        text-decoration: none;
        color: #df783d;
    }
    .ROI-conclusion{
        background-color: #FFDAC6;
        width: 100%;
        height: 90vh;
        z-index: 2;
        padding-top: 20%;
        padding-bottom: 20%;
        position: relative;
        /* padding-top: 3%; */
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }
    /* .raceByMajor{
        width: 100%;
    } */
    /* .chartRow{
        width: 50%;
        display: flex;
        flex-direction: row;
        gap: 5%;
        padding: 1rem;
        position: sticky;
        top: 50vh;
        transform: translateY(-50%);
    } */
    
    .scene{
        width: 100%;
        left: 0;
        height: auto;
        position: relative;
        
        
    }
   .info-gap{
    position: relative;
    z-index:1;
   }
    .column-wrapper {
        display: flex;
        gap: 40%; /* push children to opposite ends */
        align-items: flex-start;
        width: 100%;
        left: 0;
        z-index: 2;
        position: relative;
        /* background-color: #FFDAC6; */
    }

    .black-man,
    .white-man,
    .black-woman {
        display: flex;
        flex-direction: column;
        gap: 0;
        width: 30%; /* controls column width */
        /* background-color: rgba(255, 255, 255, 0.3); optional styling */
        /* padding: 2.5rem; */
        border-radius: 10px;
        height: auto;
        background-color: #ffdac685;
        /* box-sizing: border-box; */
    }
    h1{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        padding: 0;
        margin: 0;
        z-index: 1;
        font-size: 5vw;
        color: #df783d;
        font-family: fantasy;
        
    }
    .counter-label{
        font-size: 2.5vw;
        color: #b7a01a;
        margin-top: 0;
        
    }
    .end{
        color: #c87a2b;
        font-size: 3vw;
        font-family: fantasy;
        
    }
    .title{
        font-size: 3.5vw;
        /* color: #ab481a; */
        /* padding-bottom: 5%; */
    }
    .sub{
        font-size: 1.5vw;
        margin: 0;
        font-family: fantasy;
        color: #877512;
    }
    .fancy{
        font-family:fantasy;
        color: #98830c;
        text-shadow: 2px 2px 0 #BABD8D;
        
    }
    .fancy2{
        font-family:fantasy;
        color: #98830c;
        text-shadow: 2px 2px 0 #BABD8D;
        font-size: 3vw;
        
    }
    .equation{
        aspect-ratio: 2/1;
        width: 60%;
        height: auto;
        margin: 0;
        padding:0;
    }
    .scale{
        width: 70%;
        height: auto;
        aspect-ratio: 1.8/1;
        margin: 0;
        padding:0;
        position: relative;
        z-index: 0;
        bottom: 10%;
        /* border: 2px solid white; */
    }
    .marquee-wrapper{
    overflow: hidden;
    padding: 8vh;
}
.marquee{
    display: flex;
    width: 500%;
    flex-direction: row;
    gap: 1%;
    /* border: 2px solid white; */
    animation: scroll-left 120s linear infinite;
}
.marquee img{
    /* aspect-ratio: 1/1; */
    aspect-ratio: 1.4/1;
   height: 60vh;
   border: 8px solid #c87a2b;
   border-radius: 25px;
}
@keyframes scroll-left {
    0%{
        transform: translateX(0%);
    }
    100%{
        transform: translateX(-50%);
    }
}
    @media (max-width: 768px) {
        .ROI{
            margin-top: 10%;
            margin-bottom: 40%;
            height:auto;
            
            /* border: 2px solid white; */
        }
        .column-wrapper{
            gap: 1%;
            align-items: center;
            justify-content: center;
            margin:0;
            /* margin-top: 50%; */
            margin-bottom: 50%;
            padding: 0;
            left: 0;
            width: 95%;
        }
        .black-man,
        .white-man,
        .black-woman {
            width: 45%; /* controls column width */
            height: auto;
            background-color: #f7e9e985;
            padding: 1rem;
            left: 0;
            /* box-sizing: border-box; */
        }
        .counter-label{
            font-size: 3.8vw;
        }
        .sub{
            font-size: 2.2vw;
        }
        .ROI-conclusion{
            /* top: 155vh; */
        }
        .marquee img{
            height: 30vh;
        }
    }
   

</style>