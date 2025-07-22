<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    let options = {
        chart: {
            type: "column",
            borderRadius:20,
        },
        title: {
            text: "Poverty Percentages By Race in United States (Dec 2024)",
        },

        xAxis:{
            categories:['Black','Hispanic','Asian','White'],
            title:{
                text:'Race',
                style:{
                    FontFamily: 'Garamond',
                    fontSize: '1.5em'
                }
            }

        },
        plotOptions: {
            column: {
                allowPointSelect: true,
                dataLabels: [
                    {
                        enabled: true,
                        distance: 20,
                    },
                    {
                        enabled: true,
                        distance: -40,
                        format: "{point.percentage:.1f}%",
                        style: {
                            fontSize: "1.2em",
                            textOutline: "none",
                        },
                        filter: {
                            operator: ">",
                            property: "percentage",
                            value: 10,
                        },
                    },
                ],
            },
        },
        series: [
            {
                name: "Poverty Percentage",
                data: [
                    {
                        name: "Black",
                        y: 25,
                    },
                    {
                        name: "Hispanic",
                        sliced: true,
                        selected: true,
                        y: 29,
                    },
                    {
                        name: "Asian",
                        y: 17,
                    },
                    {
                        name: "White",
                        y: 13,
                    },
                    
                
                
                ],
            },
        ],
    };
</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <div class="chart">
                <Chart {options} highcharts={Highcharts} />
            </div>
            <p>
                Poverty percentages from Black Wealth Data Center
                <a href="https://blackwealthdata.org/explore/assets">BWDC</a> show the socieconomic disparities amongst races.
            </p>
            <p>
                 Affirmative Action aims to improve the representation of historically excluded groups in fields of education and employment. 
                This involves the preferential selection of underrepresented populations for positions on the basis of race or ethnicity.
                <a href="plato.stanford.edu/entries/affirmative-action/">Stanford Encyclopedia</a>.

            
            </p>
            <p>
                Hispanic and Black communities experience higher poverty percentages, it is thus, more common for member of these communities to have experienced financial hardship. Reducing barriers to access high-quality education could support them in breaking the cycle of poverty.
            </p>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                In 2023, the Supreme Court ruled that all university acceptance decisions must be race-blind
            </ArticleText>

            <ArticleText>
                This had previously led to a a drastic decrease in minority group admissions which could negatively impact their future prospects and limit diversity in educational institutions. <a href= "https://www.npr.org/2023/06/29/1181138066/affirmative-action-supreme-court-decision">(npr.org)</a>
            </ArticleText>

            <ArticleText>
                Affirmative Action can make educational opportunities more equitable by taking socioeconomic challenges such as poverty into consideration. 
            </ArticleText>

            <ArticleText>
                Affirmative Action recognises the systemic barriers which have made the same opportunities more difficult for individuals of marginalized racial backgrounds. 
            </ArticleText>

            <ArticleText>
                <strong>Let's now look at tuition payment statistics</strong> 
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
