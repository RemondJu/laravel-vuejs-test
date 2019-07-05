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
            this.grid.forEach(row => {
                if (true) {
                    
                }
            });
        },
        methods: {

        }
    }
</script>
