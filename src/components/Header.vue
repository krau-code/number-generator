<template>
    <div id="flex">
        <div>
            <h1>{{ header }}</h1>
            <p>for Philippine Charity Sweepstakes Office (PCSO) lotto games</p>
        </div>
        <text id="side-text">Vue Project</text>
    </div>
</template>

<script>
export default {
    data(){
        return{
            header: 'Lotto Number Generator'
        }
    }
}
</script>

<style scoped>
    #flex {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-top: 15px;
    }

    p {
        font-size: 0.8em;
        line-height: 1.6;
    }

    #side-text{
        font-size: 1em;
    }

    @media (max-width: 481px) {
        #flex {
            padding-top: 25px;
            flex-direction: column;
        }

        h1 {
            font-size: 1.5em;
            line-height: 1.2;
        }

        p {
            display: none;
        }

        #side-text {
            margin-top: 5px;
        }
    }
</style>