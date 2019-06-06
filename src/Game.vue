<template>
    <div class="game-content">
        <h1>Tic Tac Toe</h1>
        <div class="game-board" v-if="playing">
            <board @update="updateStatus" x="+" o="-"></board>
        </div>
        <div v-else>
            <h3>The winner is <span v-text="winner"></span></h3>
            <button value="Play" @click="play">Play</button>
        </div>
    </div>
</template>
<script>
    import Board from './components/Board.vue'
    export default {
        name: 'Game',
        components: {
            'board': Board
        },
        data () {
            return {
                winner: '',
                playing: true,
                rules: [
                    [[1,2,3]]
                    , [[1,4,7]]
                    , [[1,5,9]]
                    , [[2,5,8]]
                    , [[3,5,7]]
                    , [[3,6,9]]
                    , [[4,5,6]]
                    , [[7,8,9]]
                ],
            }
        },
        methods: {
            updateStatus (snap) {
                var self = this
                this.rules.some(function(rule) {
                    var status = true;
                    rule[0].every(function(position) {
                        if (snap.cells[position] != snap.symbol) {
                            status = false;
                        }
                        return status;
                    });
                    if (status) {
                        self.winner = snap.symbol;
                        self.playing = false
                    }
                    return status;
                });
            },
            play () {
                this.playing = true
            }
        }
    }
</script>
<style lang="scss" scoped>
    @import url('https://fonts.googleapis.com/css?family=Baloo+Da&display=swap');
    $baloo-da: 'Baloo Da', cursive;

    h1{
        font-family: $baloo-da;
    }

    h3{
        font-family: $baloo-da;
        font-size: 80px;

        span{
            color: red;
        }
    }

    .game-content{
        text-align: center;
        .game-board{
            width: 400px;
            height: 400px;
            margin: 20px auto;
            background: #cccccc;
        }
    }
</style>