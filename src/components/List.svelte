<script>
    import { onMount } from 'svelte';

    let data = [];
    let results = [];
    const API = "https://kittygram-api.now.sh/"

    onMount(async () => {
        const response = await fetch(API);
        let result = await response.json();
        results = result.posts;
        data = results;
        console.log('results:',results);
    });

    /* scroll configuration */
        let page = 0; 
        let size = 3;

        function prueba(){
            console.log('hola')
        }
    /* ----- */

</script>

<main>
{#each data as d}
    <div class="card">
        <div class="card-date">
            <p class="text-date">Hace 4 meses</p>
        </div>
        <div class="card-content">
            <p class="title-content">{d.username}</p>
            <div class="bag-container">
                <span class="bag">{d.postComment}</span>
            </div>
            <!--<p class="description-content">Insights is COR's new Premium Dashboards & metrics system. Organized into 4 new dashboards with over 30 new metrics. Available as a free trial.</p>-->
            <img alt="" src={d.photo} style="padding-top: 30px">
        </div>        
    </div>
{/each}

</main>

<style>
.card{
    width: 50%;
    margin-left: 25%;
    display: flex;
    padding-top: 2%;
    padding-bottom: 2%;
}

/* parte izquierda */

.card-date{
    width: 15%;
}

.text-date{
    text-align: right;
    color: #b5babe;
    font-size: .9rem;
    margin: 0%;
}

/* parte derecha */

.card-content{
    width: 65%;
    margin-left: 5%;
    border-bottom: 1px solid #f3f3f3;
}

.title-content{
    font-size: 1.55rem;
    font-weight: 500;
    padding: 0%;
    margin: 0%;
}

.bag-container{
    margin-top: 15px;
    height: 20px;
}

.bag{
    background: #82afec;
    color: white;
    font-size: 12px;
    padding: 5px 9px 5px 9px;
    border-radius: 10px;
}
/*
.description-content{
    line-height: 1.55rem;
}
*/
</style>