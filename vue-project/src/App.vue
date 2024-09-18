<template>
    <div>
        <h1>Rock Paper Scissor Game</h1>
        <div class="container">
            <div class="item" @click="winnerd(0)" ><img src="./assets/hand-paper.png" alt="">
            <p>PAPER</p></div>
            <div class="item" @click="winnerd(1)" ><img src="./assets/scissors.png" alt="">
            <p>SCISSORS</p></div>
            <div class="item" @click="winnerd(2)" ><img src="./assets/fist.png" alt="">
            <p>ROCK</p></div>
        </div>
        <div class="score">
            <div class="player">YOU: {{ player }}</div>
            <div class="computer">COMPUTER: {{ computer }}</div>
        </div>
        <div class="choices">
            <p v-if="playerchoice">👦{{ playerchoice }}</p>
            <p v-if="computerchoose">💻{{ computerchoose }}</p>
        </div>
        <div class="result" :class="{ 'Draw': winner=='DRAW' , 'win': winner=='YOU WIN' , 'loose': winner=='YOU LOSE'}">
            <p  v-if="winner=='DRAW'">{{ winner }}</p>
            <p  v-else-if="winner=='YOU WIN'">{{ winner }}</p>
            <p  v-else-if="winner=='YOU LOSE'">{{ winner }}</p>
            <p v-else> Choose</p>
        </div>
    
    </div>

</template>

<script>
export default {
    data() {
        return {
            name: 'App',
            player: 0,
            computer: 0,
            winner:null,
            playerchoice: null,
            computerchoose: null,
    }
    },
    methods: {
        computerchoice() {
            return Math.floor(Math.random() * 3)
        },
        winnerd(player) {
            
            let computer = this.computerchoice()

            if (player === computer) {
                if (player === 0 ) {
                    this.playerchoice = 'PAPER'
                    this.computerchoose = 'PAPER'
                }
                else if (player === 1 ) {
                    this.playerchoice = 'SCISSORS'
                    this.computerchoose = 'SCISSORS'
                }
                else if (player === 2 ) {
                    this.playerchoice = 'ROCK'
                    this.computerchoose = 'ROCK'
                }
                this.winner =  'DRAW'
            } else if (player === 0 && computer === 1){
                this.playerchoice = 'PAPER'
                this.computerchoose = 'SCISSORS'
                this.computer++
                this.winner =  'YOU LOSE'}
            else if(player === 1 && computer === 2) {
                this.playerchoice = 'SCISSORS'
                this.computerchoose = 'ROCK'
                this.computer++
                this.winner =  'YOU LOSE'
            }
            else if  (player === 2 && computer === 0) {
                this.playerchoice = 'ROCK'
                this.computerchoose = 'PAPER'
                this.computer++
                this.winner =  'YOU LOSE'
            }
            else if (computer === 0 && player === 1){
                this.computerchoose = 'PAPER'
                this.playerchoice = 'SCISSORS'
                this.player++
                this.winner =  'YOU WIN'}
            else if(computer === 1 && player === 2) {
                this.computerchoose = 'SCISSORS'
                this.playerchoice = 'ROCK'
                this.player++
                this.winner =  'YOU WIN'
            }
            else if  (computer === 2 && player === 0) {
                this.computerchoose = 'ROCK'
                this.playerchoice = 'PAPER'
                this.player++
                this.winner =  'YOU WIN'
            }
            
        }

        
    }
}
</script>
<style >

h1 {
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2.5rem;
    padding: 0.5rem;
    background-color: rgb(104, 213, 227);
}

.container {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 2rem;

}
.container .item {
    padding: 0.5rem;
}
.container .item  p{
    font-size: 1rem;
    text-align: center;
    font-weight: bold;
    margin-top: 0.5rem;  
}

.container .item img {
    box-shadow: 2px 2px 2px black, -4px -4px 2px rgb(104, 213, 227);
    width: 7rem;
    height: 7rem;
    border: 3px solid black;
    /* border-radius: 50%; */
    padding: 15px;
    object-fit: fill;
    cursor: pointer;
}
img {
    width: 100%;
    height: 100%;
}
.score{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    margin-top: 2rem;
    font-size: 1.5rem;
    font-weight: bold;
}

.result{
    width: 200px;
    text-align: center;
    font-size: 2rem;
    font-weight: bold;
    margin: auto;
    margin-top: 2rem;
    padding: 0.5rem;
    border: 2px solid black; 
    border-radius: 0.5rem;  
}

.win {
    background-color: green;
    color: aliceblue;
    padding: 0;

}

.loose {
    background-color: red;
    color: aliceblue;
    padding: 0;
    
}

.Draw {
    background-color: rgb(78, 179, 222);
    color: aliceblue;
    padding: 0;
    
}

.choices {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    margin-top: 2rem;
    font-size: 1rem;
    font-weight: bold;
}


</style>
