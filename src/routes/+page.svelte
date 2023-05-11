
<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@500&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@500&family=Permanent+Marker&display=swap" rel="stylesheet">
    <title>
        Days Since Last Pump Died
    </title>
</svelte:head>


<script>
    import { onMount } from "svelte";

    let diff = 0;
    
    function getDaysDifference(date1, date2){
        const diffTime = Math.abs(date2 -date1);
        return Math.ceil(diffTime / (60 * 60 * 24 * 1000))
    }
    
    onMount(() => {
        let lastPumpDiedOn = new Date('5/11/2023')
        let currentDate = new Date()
        
        diff = getDaysDifference(currentDate, lastPumpDiedOn);

    });

</script>

<div class="container">
    <span class="text-title">Days since last pump died </span>
    <span class="text-days">{diff}</span>
</div>



<style>

.text-title{
    font-size: 48px;
    margin: 20px;
    color: #084a84;
}

.text-days{
    font-size: 48px;
    color: #fdd10b;
    font-family: 'Permanent Marker', cursive;
}

:global(body){
    height: 100%;
    margin: 0;
    padding: 0;
}

.container{
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    padding-top: 100px;
    margin: 0;
    font-family: 'Open Sans', sans-serif;
}

</style>