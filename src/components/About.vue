<template>
    <div>
        <button @click="fetchData">Fetch Data</button>
        <div v-if="loading">Loading...</div>
        <div v-else>
            <h2>Data:</h2>
            <ul>
                <li v-for="item in data" :key="item.id">{{ item.title }}</li>
            </ul>
        </div>
    </div>
  </template>
  
  <script>
    import axios from 'axios';
    
    export default {
        name: 'About',
        components: {
        },
        
        data(){
            return {
                initialState: 'asdasd',
                loading: false,
                data: []
            }
        },
        mounted() {
            this.callConsole()
        },
        methods: {
            callConsole(){
                console.log(this.initialState)
            },
            async fetchData() {
                this.loading = true;
                try {
                    const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
                    this.data = response.data;
                } catch (error) {
                    console.error('Error fetching data:', error);
                } finally {
                    this.loading = false;
                }
            },
        }
    }
  </script>
  