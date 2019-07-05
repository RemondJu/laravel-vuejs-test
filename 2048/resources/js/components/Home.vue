<template>
    <v-container>
        <v-layout column>
            <v-flex>
                <h1>2048</h1>
            </v-flex>
            <v-flex>
                <v-layout v-for="(row, index) in grid" row :key="index" >
                    <v-flex v-for="(tile, index) in row" :key="index">{{ tile }}</v-flex>
                </v-layout>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    export default {
        data () {
            return {
                grid: [
                    [0, 0, 0, 0],
                    [0, 0, 0, 0],
                    [0, 0, 0, 0],
                    [0, 0, 0, 0],
                ],
                rowValues: []
            }
        },
        created () {
            // Initiliazing two randomly placed tokens
            for (let i = 0; i < 2; i++) {
                let randrow = Math.random() * 4
                let randTile = Math.random() * 4
                this.grid[Math.floor(randrow)][Math.floor(randTile)] = 2
            }
        },
        methods: {
            // creating a new row if movement happened
            moveRight() {
                let newGrid = []
                this.grid.forEach(row => {
                    let newRow = [0, 0, 0, 0]
                    row.forEach((tile, index) => {
                        if (index < 2) {
                            newRow[index+1] = tile
                        }
                        else if (index === 2) {
                            newRow[index + 1] = row[index+1] + tile
                        }
                    })
                    newGrid.push(newRow)
                });
                this.grid = newGrid
                console.log(this.grid)
            },
            moveLeft() {
                console.log('moved left')
            },
            moveUp() {
                console.log('moved up')
            },
            moveDown() {
                console.log('moved down')
            },
        },
        mounted() {
            let that = this
            window.addEventListener('keydown', function(e) {
                if (e.keyCode === 39) {
                    that.moveRight()
                }
                if (e.keyCode === 37) {
                    that.moveLeft()
                }
                if (e.keyCode === 38) {
                    that.moveUp()
                }
                if (e.keyCode === 40) {
                    that.moveDown()
                }
            });
        }
    }
</script>
