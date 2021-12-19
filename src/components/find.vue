<template>
    <div class="find" v-if="show">
        <div class="find__top">
            <div class="find__top-button"><button><img src="/img/left.png" alt="img" />Back</button></div>
        </div>
        <div data-simplebar class="find__content">
            <div :class="item.class" v-for="item in content" :key="item.name">
                <div class="find__block-img"><img :src="item.pic" alt="img" /></div>
                <div class="find__block-info">
                    <div class="find__block-top">
                        <div class="find__block-text">{{item.name}}</div>
                        <div :class="item.grow ? 'find__block-index' : 'find__block-index-red'" v-if="item.num"><img class="find__block-index-img" v-if="item.img" :src="item.img" alt="img" /> {{item.num}}</div>
                    </div>
                    <div class="find__block-subtext">{{item.subtext}}</div>
                </div>
                <div class="find__block-jobs">{{item.jobs}}</div>
            </div>
        </div>
        <div class="find__bottom">
            <div class="find__bottom-info">
                <div class="find__info-text">$70,600 a year</div>
                <div class="find__info-subtext">Avarage salary</div>
            </div>
            <div class="find__bottom-btns">
                <button class="find__bottom-clear">Clear</button>
                <button class="find__bottom-show">Show 3129 vacancies</button>
            </div>
        </div>
        <div class="find__close"><button @click="closeFind()"><img src="/img/cancel.png" alt="img" /></button></div>
        <div class="find__tool"><img class="find__tool-img" src="/img/play.png" alt="img" /></div>
    </div>
</template>

<script>
    import "../assets/simplebar.js";
    import "../assets/simplebar.css";
    export default {
        name: "find",
        props: ["showFind", "find"],
        data() {
            return {
                show: false,
                content: [
                    {class: "find__block", grow: true, pic: "/img/list.png", name: "Testing software", img: "/img/up.png", num: "48.7%", subtext: "Task", jobs: "10 jobs"},
                    {class: "find__block", grow: false, pic: "/img/user.png", name: "Test Engineer", img: false, num: false, subtext: "Position", jobs: "4 jobs"},
                    {class: "find__block", grow: false, pic: "/img/list.png", name: "Testing Code", img: "/img/down.png", num: "18.6%", subtext: "Task", jobs: "3 jobs"},
                    {class: "find__block", grow: false, pic: "/img/list.png", name: "Testing email campaings", img: false, num: false, subtext: "Task", jobs: "3 jobs"},
                    {class: "find__block", grow: true, pic: "/img/list.png", name: "Testing new products", img: "/img/up.png", num: "0.6%", subtext: "Task", jobs: "3 jobs"},
                    {class: "find__block", grow: true, pic: "/img/list.png", name: "Testing software", img: "/img/up.png", num: "48.7%", subtext: "Task", jobs: "10 jobs"},
                    {class: "find__block", grow: false, pic: "/img/user.png", name: "Test Engineer", img: false, num: false, subtext: "Position", jobs: "4 jobs"},
                    {class: "find__block", grow: false, pic: "/img/list.png", name: "Testing Code", img: "/img/down.png", num: "18.6%", subtext: "Task", jobs: "3 jobs"},
                    {class: "find__block", grow: false, pic: "/img/list.png", name: "Testing email campaings", img: false, num: false, subtext: "Task", jobs: "3 jobs"},
                    {class: "find__block", grow: true, pic: "/img/list.png", name: "Testing new products", img: "/img/up.png", num: "0.6%", subtext: "Task", jobs: "3 jobs"}
                ]
            }
        },
        methods: {
            closeFind() {
                this.show = false;
                this.$emit("close", false);
            }
        },
        watch: {
            showFind: function() {
                this.show = this.showFind;
            },
            find: function() {
                let val = this.find.trim();
                if(val != "") {
                    this.content.filter(function(elem) {
                        if(elem.name.search(val) == -1) {
                            elem.class = "find__block-hidden";
                            return elem;
                        }
                        else {
                            elem.class = "find__block";
                            return elem;
                        }
                    })
                }
                else {
                    this.content.filter(function(elem) {
                        elem.class = "find__block";
                        return elem;
                    })
                }
            }
        }
    }
</script>

<style scoped>
    .display {
        display: block;
    }
    .find {
        max-width: 820px;
        background-color: #ffffff;
        padding: 25px;
        margin: 15px auto;
        position: relative;
        border-radius: 20px;
    }
    .find__block-bottom {
        display: flex;
    }
    .find__close {
        width: 22px;
        height: 22px;
        position: absolute;
        top: 19px;
        right: 19px;
    }
    .find__close button {
        width: 22px;
        height: 22px;
        border: transparent;
        background-color: transparent;
        cursor: pointer;
    }
    .find__close button img {
        width: 22px;
        height: 22px;
    }
    .find__tool {
        width: 35px;
        height: 13px;
        position: absolute;
        top: -13px;
        left: 50%;
        transform: translateX(-50%);
    }
    .find__tool img {
        width: 35px;
        height: 13px;
    }
    .find__bottom {
        padding-top: 20px;
        display: flex;
        justify-content: space-between;
    }
    .find__info-text {
        color: #29abe2;
        margin-bottom: 7px;
    }
    .find__info-subtext {
        color: #7f7f7f;
    }
    .find__bottom-clear {
        padding: 17px 35px;
        border: 1px solid #ededed;
        border-radius: 30px;
        background-color: transparent;
        cursor: pointer;
        margin-right: 10px;
        color: #7f7f7f;
    }
    .find__bottom-show {
        padding: 18px 70px;
        background-color: #29abe2;
        border: 1px solid #29abe2;
        border-radius: 30px;
        color: #ffffff;
        cursor: pointer;
        font-weight: bold;
    }
    .find__top {
        padding: 0 25px 25px;
        margin-left: -25px;
        margin-right: -25px;
        border-bottom: 1px solid #f2f2f2;
    }
    .find__top-button button {
        background-color: transparent;
        border: none;
        color: #29abe2;
        cursor: pointer;
    }
    .find__top-button button img {
        width: 17px;
        height: 15px;
        transform: translate(-5px, 3px);
    }
    .find__content {
        margin-left: -25px;
        height: 370px;
    }
    .find__block {
        position: relative;
        padding: 19px 36px 24px;
        display: flex;
        border-bottom: 1px solid #f2f2f2;
    }
    .find__block-hidden {
        position: relative;
        padding: 19px 36px 24px;
        display: flex;
        border-bottom: 1px solid #f2f2f2;
        display: none;
    }
    .find__block-img {
        width: 27px;
        height: 23px;
        margin-right: 24px;
        transform: translateY(7px);
    }
    .find__block-img img {
        width: 27px;
        height: 23px;
    }
    .find__block-top {
        display: flex;
    }
    .find__block-index {
        margin-left: 12px;
        color: #39b54a;
    }
    .find__block-index-red {
        margin-left: 12px;
        color: #ef383f;
    }
    .find__block-index-img {
        width: 10px;
        height: 16px;
        transform: translateY(2px);
    }
    .find__block-jobs {
        position: absolute;
        top: 50%;
        right: 20px;
        transform: translateY(-50%);
    }
</style>