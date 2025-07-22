<script>
    let { title, subtitle } = $props();
</script>

<div class="title-card">
    <div class="content">
        <h1>{title}</h1>
        <p>{subtitle}</p>
    </div>
</div>

<style>
    .title-card {
        background-color: #207e8f;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 2rem;
        box-sizing: border-box;
        font-family: "Garamond", sans-serif;
        background-image: url('graduationcanva.png');
    }

    .content {
        max-width: 700px;
        padding: 2rem;

    
    }

    h1 {
        font-size: 4rem;
        margin: 0;
        color: #ffffff;
        text-shadow: 1px 1px 0 #5177a6;
    }

    p {
        font-size: 1.3rem;
        color: #f7f5eb;
        margin-top: 1rem;
    }

    @media (max-width: 600px) {
        h1 {
            font-size: 2.2rem;
        }

        p {
            font-size: 1.1rem;
        }
    }
</style>
