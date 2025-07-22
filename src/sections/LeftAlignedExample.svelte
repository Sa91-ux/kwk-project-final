<script>
// @ts-nocheck

    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const series = [
        {
            name: "Group 1",
            data: [
                [1990, 3],
                [2000, 4],
                [2010, 1],
                [2020, 1],
            ],
            color: "#8427c9",
        },
        {
            name: "Group 2",
            data: [
                [1990, 2],
                [2000, 5],
                [2010, -2],
                [2020, 2],
            ],
            color: "#ff99fc",
        },
        {
            name: "All Groups",
            data: [
            ],
            color: "#4096fa",
        },
    ];

    let chart;
    let thirdSeriesVisible = false;

    let options = {
        chart: {
            type: "column",
            backgroundColor: "#ffffff",
            borderColor: "#007052",
            borderWidth: 1,
            borderRadius: 20,
        },
        title: {
            text: "Percentage of 18-28 yr olds by race that received support to pay tuition (2021)",
            fontSize: 1.55,
        }, 
        xAxis:{
            categories:['Black','Hispanic','White']
        },
        series:[
            {
                name:"% that received tuition payment aid",
                data: [
                 {
                        y:10.2,
                    },
                {
                    y:8.0,
                },{
                    y:17.2,
                },
                ]
            },

            ],
        
        
        
    };


</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <div class="chart">
                <Chart bind:chart {options} highcharts={Highcharts} />
            </div>
            
            <div>
                <p>
                    This chart indicates the differences in percentages that receive support in funding their education. <a href=" https://blackwealthdata.org/explore/assets"> (BWDC) </a>
                </p>
                <p>
                    This statistic suggests that minority groups experience greater educational disadvantages due to the lack of financial assistance. Similarly, on average, minority groups inherit less money from their families. 
                </p>
                <p>
                    <strong
                        >63% out of 194 studies on the effectiveness of affirmative action demonstrated positive results on the livelihoods of racial minorities</strong> <a href = "unu.edu/article/affirmativr-action-policies-increase-diversity-are-successful-controversial-around-world"> (United Nations University)</a>
                    
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                Despite evidence demonstrating the systematic barriers faced by minority groups, Affirmative Action remains a controversial topic 
            </ArticleText>

            <ArticleText>
                Public opinion in the United States is divided on the implementational of race-based preferential selection
            </ArticleText>

            <ArticleText>
                In 2022, <strong> 36%</strong> of survey respondents supported Affirmative Action and <strong>29%</strong> were against it <a href="https://www.pewresearch.org/short-reads/2023/06/16/americans-and-affirmative-action-how-the-public-sees-the-consideration-of-race-in-college-admissions-hiring/">(Pew Research Center)</a>
            </ArticleText>

            <ArticleText>
                <strong>
                    Wealth inequalities still remain prevalent
                </strong>
            </ArticleText>

        
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        margin: 0px auto;
    }


    
    
</style>
