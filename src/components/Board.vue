<template>
    <div class="board-content">
        <div class="cell">
            <piece :symbol="cells[1]" @tap="onTap(1)"></piece>
        </div>
        <div class="cell">
            <piece :symbol="cells[2]" @tap="onTap(2)"></piece>
        </div>
        <div class="cell">
            <piece :symbol="cells[3]" @tap="onTap(3)"></piece>
        </div>
        <div class="cell">
            <piece :symbol="cells[4]" @tap="onTap(4)"></piece>
        </div>
        <div class="cell">
            <piece :symbol="cells[5]" @tap="onTap(5)"></piece>
        </div>
        <div class="cell">
            <piece :symbol="cells[6]" @tap="onTap(6)"></piece>
        </div>
        <div class="cell">
            <piece :symbol="cells[7]" @tap="onTap(7)"></piece>
        </div>
        <div class="cell">
            <piece :symbol="cells[8]" @tap="onTap(8)"></piece>
        </div>
        <div class="cell">
            <piece :symbol="cells[9]" @tap="onTap(9)"></piece>
        </div>
    </div>
</template>
<script>
    import Piece from './Piece.vue'
    export default {
        name: 'board',
        components: {
            Piece
        },
        data () {
            return {
                cells: {
                    1: '', 2: '',3: '',4: '',5: '',6: '',7: '',8: '',9: '',
                },
                symbol: {
                    x: 'X',
                    o: 'O'
                },
                nextSymbol: 'x'
            }
        },
        props: {
            x: {
                type: String,
                default: 'X'
            },
            o: {
                type: String,
                default: 'O'
            }
        },
        mounted () {
            this.symbol.x = this.x
            this.symbol.o = this.o
        },
        methods: {
            onTap (position) {
                if (this.cells[position] == ''){
                    this.cells[position] = this.symbol[this.nextSymbol]
                    this.updateNextSymbol()
                    this.$emit("update", {
                        cells: this.cells,
                        symbol: this.cells[position]
                    })
                }
            },
            updateNextSymbol () {
                if ( this.nextSymbol == 'x' ) {
                    this.nextSymbol = 'o'
                } else {
                    this.nextSymbol = 'x'
                }
            }
        }
    }
</script>
<style lang="scss" scoped>
    .board-content{
        height: 100%;
        background: #555555;
        display: grid;
        grid-template-columns: 33.33% 33.33% 33.33%;
        grid-template-rows: 33.33% 33.33% 33.33%;

        .cell{
            align-self: stretch;
            border: #ffffff 3px solid;
        }
    }
</style>