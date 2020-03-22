<template>
    <div>
        <input v-on:input="onInput"/>
        <button v-on:click="onClick">Search</button>
    </div>
</template>



<script>
export default {
    name: 'SearchBar',
    data: function(){
        return {
            inputValue: ''
        }
    },
    methods: {
        onInput: function(event){
            // this.$emit('termChange',event.target.value);

            this.inputValue = event.target.value;

        },
        onClick:function(){
            this.$emit('searchTerm',this.inputValue);
        }
    }
}
</script>

<style scoped>
input {
    width:75%;
}

div {
    text-align: center;
    margin:20px;
}
</style>