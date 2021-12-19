<template>
    <div class="search">
        <div class="search__inner">
            <div class="search__title"><h1>It`s time to find <span>the perfect job</span></h1></div>
            <div class="search__input">
                <input @click="display = true" v-model="find" type="text" placeholder="Search by anything" />
                <img class="search__input-img" src="/img/search.png" alt="img"/>
                <div class="input__close" v-if="showFind"><button @click="closeSearch()"><img src="/img/cancel.png" alt="img" /></button></div>
            </div>
            <img class="search__img" src="/img/bg.jpg" alt="img" />
        </div>
        <Filtr :display="display" @close="display = false"/>
        <Find :showFind="showFind" :find="find" @close="closeSearch()"/>
    </div>    
</template>

<script>
    import Filtr from "../components/filtr.vue";
    import Find from "../components/find.vue";
    export default {
        name: "search",
        components: {
            Filtr, Find
        },
        data() {
            return {
                display: false,
                showFind: false,
                find: ""
            }
        },
        methods: {
            closeSearch() {
                this.find = "";
                this.showFind = false;
            }
        },
        watch: {
            find: function() {
                if(this.find != "") {
                    this.display = false;
                    this.showFind = true;
                }
            }
        }
    }
</script>

<style scoped>
    .search {
        position: relative;
        height: 950px;
        margin-top: -21px;
    }
    .search__img {
        position: absolute;
        z-index: -1;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        height: 100%;
        width: 100%;
    }
    .search__title {
        text-align: center;
        padding-top: 50px;
    }
    .search__title h1 span {
        color:#d55527;
    }
    .search__input {
        margin: 0 auto;
        width: 565px;
        height: 70px;
        position: relative;
    }
    .search__input input {
        width: 475px;
        height: 70px;
        background-color: #fcfcfc;
        border: transparent;
        border-radius: 50px;
        padding-left: 70px;
        padding-right: 20px;
    }
    .search__input-img {
        position: absolute;
        width: 20px;
        height: 20px;
        top: 50%;
        transform: translateY(-50%);
        left: 30px;
    }
     .input__close {
        width: 22px;
        height: 22px;
        position: absolute;
        top: 50%;
        right: 22px;
        transform: translateY(-50%);
    }
    .input__close button {
        width: 22px;
        height: 22px;
        border: transparent;
        background-color: transparent;
        cursor: pointer;
    }
    .input__close button img {
        width: 22px;
        height: 22px;
    }
</style>
