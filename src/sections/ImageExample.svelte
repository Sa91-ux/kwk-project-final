<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    
</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <img class="SCF" src="SCF.png" alt="Asset Graph" />
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                <strong>
                    Even in the 99th Percentile of total assets, minority groups have a much lower valuation.
                </strong>
            </ArticleText>

            <ArticleText> Imagine the differences in opportunities accessible to each group... </ArticleText>
            <ArticleText> Degree attainment levels vary vastly between different racial groups. <a  href="blackwealthdata.org/explore/education">(BWDC)</a></ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .SCF {
        width: 150%;
        margin: 0px auto;
        border-width: 1;
        border-radius: 20;
    }
</style>

