<script>
    import { onMount } from "svelte";

    let diff = 0;

    function getDaysDifference(date1, date2) {
        const diffTime = Math.abs(date2 - date1);
        return Math.ceil(diffTime / (60 * 60 * 24 * 1000));
    }

    onMount(() => {
        let lastPumpDiedOn = new Date("5/11/2021");
        let currentDate = new Date();

        diff = getDaysDifference(currentDate, lastPumpDiedOn);
    });
</script>

<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
        href="https://fonts.googleapis.com/css2?family=Cabin+Sketch:wght@400;700&family=Londrina+Sketch&display=swap"
        rel="stylesheet"
    />
    <link rel="stylesheet" href="/reset.css" />
    <title>Days Since Last Pump Died</title>
</svelte:head>

<div class="chalkboard-region">
    <div class="chalkboard-pin" />
    <div class="chalkboard-hanger" />
    <div class="chalkboard">
        <span class="text-title">Days since last pump died </span>
        <span class="text-days">{diff}</span>
    </div>
</div>

<style>
    .text-title {
        font-size: 64px;
        text-align: center;
        margin: 20px;
        color: #ffffff;
    }

    .text-days {
        font-size: 96px;
        font-weight: bold;
        color: #ffbf00;
        font-family: "Cabin Sketch", cursive;
    }

    :global(body) {
        min-height: 100vh;
        display: grid;
        justify-content: center;
    }

    .chalkboard-region {
        display: flex;
        flex-direction: column;
        align-items: center;
        height: min-content;
        /* outline: red solid 1px; */
    }

    .chalkboard-pin {
        position: absolute;
        background-color: #ffbf00;
        border-radius: 50%;
        height: 16px;
        width: 16px;
        z-index: 1;
    }

    .chalkboard-hanger {
        position: absolute;
        border: 3px solid;
        border-color: grey transparent transparent grey;
        height: 150px;
        width: 150px;
        transform: rotateZ(45deg) translate(15%, 15%);
    }

    .chalkboard {
        background-color: black;
        border: solid 10px;
        border-color: #964b00 #6d3700 #482400 #7c3e00;
        max-width: 32em;
        max-height: 28em;
        margin-top: 106px;
        display: flex;
        flex-direction: column;
        flex-shrink: inherit;
        align-items: center;
        justify-content: center;
        font-family: "Cabin Sketch", sans-serif;
    }
</style>
