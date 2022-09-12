<template>
    <div>
        <h1>{{ header }}</h1>
        <p>for Philippine Charity Sweepstakes Office (PCSO) lotto games</p>
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
    div {
        margin: 30px auto;
        padding: 0 25px;
    }

    h1,p {
        text-align: center;
    }

    p {
        font-size: 0.8em;
        line-height: 1.6;
    }

    @media (max-width: 481px) {
      h1 {
        line-height: 1.2;
      }

      p{
        margin-top: 12px;
      }
    }
</style>