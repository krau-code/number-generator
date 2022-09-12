<template>
    <form @submit.prevent="generate">
        <select v-model="chosenGame">
            <option value="" disabled selected>Choose a Lotto Game</option>
            <option v-for="game in lottoGames" :key="game.id" :value="game.id">{{ game.name }}</option>  
        </select>
        <button>Generate Number</button>
    </form>
    <p class="error">{{ error }}</p>
</template>

<script>
export default {
    props: [ 'lottoGames' ],
    data() {
        return {
            chosenGame: '',
            error: ''
        }
    },
    methods: {
        generate(){
            if (!this.chosenGame) {
                this.error = "please choose a lotto game first";
            } else {
                this.$emit('generate', this.chosenGame);
                this.error = "";
            }
        }
    },
    emits: ['generate']
}
</script>

<style scoped>
    form {
        display: flex;
        justify-content: center;
        margin: 50px auto 30px auto;
    }

    form select,
    form button {
        -webkit-box-shadow: 5px 5px 20px -8px rgba(0,0,0,0.3);
        -moz-box-shadow: 5px 5px 20px -8px rgba(0,0,0,0.3);
        box-shadow: 5px 5px 20px -8px rgba(0,0,0,0.3);
    }

    form select{
        color: #222831;
        background: #eee;
        font-family: 'Poppins', sans-serif;
        padding: 5px;
        border: 0;
        min-width: 200px;
        border-radius: 5px;
    }

    form select:focus {
        outline: none;
    }

    form button {
        color: #222831;
        font-family: 'Poppins', sans-serif;
        background: #00ADB5;
        padding: 5px 10px;
        border: 0;
        border-radius: 5px;
        margin-left: 30px;
    }

    form button:hover {
        background: #029ea6;
    }

    .error { 
        text-align: center;
        color: #ff6961;
    }

    @media (max-width: 481px) {
        form {
            display: grid;
        }

        form select {
            width: 100%;
            margin-left: auto;
            margin-right: auto;
        }

        form button {
            width: 100%;
            margin-left: auto;
            margin-right: auto;
            margin-top: 20px;
        }
    }
</style>