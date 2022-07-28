<template>
    <input type="text" v-model="searchText" @keyup.enter="setSearchText">
</template>

<script>

export default{
    name: 'BaseHeader',
    data(){
        return{
            searchText: '',
        }
    },
    methods:{
        setSearchText(){
            this.$emit('search-text', this.searchText)
            console.log(this.searchText)
        }
    }
}
</script>

<style lang="scss" scoped>
</style>