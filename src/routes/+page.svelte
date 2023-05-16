<script>
    import { onMount } from "svelte";

    let diff = 0;

    function getDaysDifference(date1, date2) {
        const diffTime = Math.abs(date2 - date1);
        return Math.ceil(diffTime / (60 * 60 * 24 * 1000));
    }

    onMount(() => {
        let lastPumpDiedOn = new Date("5/11/2023");
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

<div class="room">
    <div class="whiteboard-region">
        <div class="whiteboard-pin" />
        <div class="whiteboard-hanger" />
        <div class="whiteboard">
            <span class="text-title">Days since last pump died </span>
            <span class="text-days">{diff}</span>
        </div>
    </div>
    <div class="walls">
        <div class="wall-left" />
        <div class="wall-right">
            <div class="wall-right-logs" />
        </div>
        <div class="wall-bottom" />
    </div>
</div>

<style>
    .text-title {
        font-size: 64px;
        text-align: center;
        font-weight: bold;
        margin: 20px;
        color: #11497b;
    }
    .text-days {
        font-size: 96px;
        font-weight: bold;
        color: #ffae00;
        font-family: "Cabin Sketch", cursive;
    }

    :global(body) {
        min-height: 100vh;
        display: grid;
        justify-content: center;
    }

    .walls {
        position: absolute;
        top: 0;
        left: 0;
        background-color: #165d9c;
        height: 100vh;
        width: 100vw;
        z-index: -1;
    }

    .wall-left {
        position: absolute;
        background-color: #11497b;
        height: 100vh;
        width: 50vw;
        z-index: 0;
        transform-origin: 0 0;
        transform: perspective(100vw) rotateY(45deg);
    }

    .wall-right {
        position: absolute;
        top: 0;
        right: 0;
        background-color: #11497b;
        height: 100vh;
        width: 50vw;
        z-index: 0;
        transform-origin: 100% 0;
        transform: perspective(100vw) rotateY(-45deg);
    }

    .wall-bottom {
        position: absolute;
        bottom: 0;
        left: 0;
        background-color: #8b6534;
        height: 78vh;
        width: 100vw;
        z-index: 0;
        transform-origin: 50% 100%;
        transform: perspective(50vh) rotateX(45deg);
    }
    .whiteboard-region {
        display: flex;
        flex-direction: column;
        align-items: center;
        height: min-content;
    }

    .whiteboard-pin {
        position: absolute;
        background-color: #ffbf00;
        border-radius: 50%;
        height: 16px;
        width: 16px;
        z-index: 3;
    }

    .whiteboard-hanger {
        position: absolute;
        border: 3px solid;
        border-color: grey transparent transparent grey;
        height: 150px;
        width: 150px;
        transform: rotateZ(45deg) translate(15%, 15%);
    }

    .whiteboard {
        background-color: white;
        border: solid 8px;
        border-color: #9b9b9b #5f5f5f #3b3b3b #5f5f5f;
        width: 45vw;
        min-height: 45vh;
        margin-top: 106px;
        display: flex;
        flex-direction: column;
        flex-shrink: inherit;
        align-items: center;
        justify-content: center;
        font-family: "Cabin Sketch", sans-serif;
    }
</style>
