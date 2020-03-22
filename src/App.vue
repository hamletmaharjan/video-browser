<template>
<div class="container">
    <SearchBar v-on:searchTerm="onSearchTerm"></SearchBar>
    <VideoList v-bind:videos="videos" v-on:videoSelect="onVideoSelect"></VideoList>
</div>

</template>


<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
const API_KEY = 'AIzaSyAs3kBHy4iyvqcSeIAvWm7BoAyfe50scsU';

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList
    },
    data: function(){
        return {
            videos:[]
        };
    },
    methods: {
        onVideoSelect(video) {
            console.log(video);
        },
        onSearchTerm: function(searchTerm){
            console.log(searchTerm);
            axios.get('https://www.googleapis.com/youtube/v3/search',{
                params:{
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items
            });
        }
    }
}
</script>