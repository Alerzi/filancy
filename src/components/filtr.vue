<template>
    <div class="filtr" v-if="show">
        <div class="filtr__block">
            <div class="filtr__block-title"><h2>Location</h2></div>
            <div class="filtr__block-btns">
                <button @click="selectLocation(index)" v-for="(item, index) in location" :key="item.name" :class="item.class">{{item.name}}</button>
                <button class="filtr__block-more">Show More</button>
            </div>
        </div>
        <div class="filtr__block">
            <div class="filtr__block-title"><h2>Requirements</h2></div>
            <div class="filtr__block-btns">
                <button @click="selectRequerments(index)" v-for="(item, index) in requerments" :key="item.name" :class="item.class">{{item.name}}</button>
                <button class="filtr__block-more">Show More</button>
            </div>
        </div>
         <div class="filtr__block">
            <div class="filtr__block-title"><h2>Tasks</h2></div>
            <div class="filtr__block-btns">
                <button @click="selectTasks(index)" v-for="(item, index) in tasks" :key="item.name" :class="item.class">{{item.name}}</button>
                <button class="filtr__block-more">Show More</button>
            </div>
        </div>
        <div class="filtr__block-bottom">
            <div class="filtr__block">
                <div class="filtr__block-title"><h2>Required experience</h2></div>
                <div class="filtr__block-btns">
                    <button @click="selectExperience(index)" v-for="(item, index) in experience" :key="item.name" :class="item.class">{{item.name}}</button>
                </div>
            </div>
            <div class="filtr__block">
                <div class="filtr__block-title"><h2>More</h2></div>
                <div class="filtr__block-btns">
                    <button class="filtr__block-more" v-for="item in more" :key="item">{{item}}</button>
                </div>
            </div>
        </div>
        <div class="filtr__keys">
            <div class="filtr__key">
                <div class="filtr__key-item">Esc</div>
                <div class="filtr__key-text">Close</div>
            </div>
            <div class="filtr__key">
                <div class="filtr__key-item">Enter</div>
                <div class="filtr__key-text">Choose</div>
            </div>
            <div class="filtr__key">
                <div class="filtr__key-item"><img class="filtr__key-up" src="/img/arrow.png" alt="img"/></div>
                <div class="filtr__key-item"><img class="filtr__key-down" src="/img/arrow.png" alt="img"/></div>
                <div class="filtr__key-text">Move</div>
            </div>
            <div class="filtr__key">
                <div class="filtr__key-item">Space</div>
                <div class="filtr__key-text">Apply</div>
            </div>
        </div>
        <div class="filtr__bottom">
            <div class="filtr__bottom-info">
                <div class="filtr__info-text">$70,600 a year</div>
                <div class="filtr__info-subtext">Avarage salary</div>
            </div>
            <div class="filtr__bottom-btns">
                <button @click="resetFiltr()" class="filtr__bottom-clear">Clear</button>
                <button class="filtr__bottom-show">Show 3129 vacancies</button>
            </div>
        </div>
        <div class="filtr__close"><button @click="closeFiltr()"><img src="/img/cancel.png" alt="img" /></button></div>
        <div class="filtr__tool"><img class="filtr__tool-img" src="/img/play.png" alt="img" /></div>
    </div>
</template>

<script>
    export default {
        name: "filtr",
        props: ["display"],
        data() {
            return {
                location: [
                    {name: "New York", class: "filtr__block-btn", selected: false},
                    {name: "Remote", class: "filtr__block-btn", selected: false},
                    {name: "Los Angeles", class: "filtr__block-btn", selected: false},
                    {name: "Chicago", class: "filtr__block-btn", selected: false}
                ],
                requerments: [
                    {name: "Communication", class: "filtr__block-btn", selected: false},
                    {name: "Microsoft Excel", class: "filtr__block-btn", selected: false},
                    {name: "Microsoft Word", class: "filtr__block-btn", selected: false}
                ],
                tasks: [
                    {name: "Answering phone calls", class: "filtr__block-btn", selected: false},
                    {name: "Providing customer service", class: "filtr__block-btn", selected: false},
                    {name: "Creating reports", class: "filtr__block-btn", selected: false}
                ],
                experience: [
                    {name: "0", class: "filtr__block-btn", selected: false},
                    {name: "1 year", class: "filtr__block-btn", selected: false},
                    {name: "3 years", class: "filtr__block-btn", selected: false},
                    {name: "5+ years", class: "filtr__block-btn", selected: false}
                ],
                more: ["Positions", "Companies", "Benefits"],
                show: false,
            }
        },
        methods: {
            closeFiltr() {
                this.show = false;
                this.$emit('close', false);
            },
            resetFiltr() {
                this.location.filter((item) => {
                    item.class = "filtr__block-btn";
                    item.selected = false;
                    return item;
                });
                this.requerments.filter((item) => {
                    item.class = "filtr__block-btn";
                    item.selected = false;
                    return item;
                });
                this.tasks.filter((item) => {
                    item.class = "filtr__block-btn";
                    item.selected = false;
                    return item;
                });
                this.experience.filter((item) => {
                    item.class = "filtr__block-btn";
                    item.selected = false;
                    return item;
                });
            },
            selectLocation(index) {
                let item = this.location.splice(index,1);
                if(item[0].selected == false) {
                    item[0].selected = true;
                    item[0].class = "filtr__block-btn-active";
                    this.location.unshift(item[0]);
                }
                else {
                    item[0].selected = false;
                    item[0].class = "filtr__block-btn";
                    this.location.push(item[0]);
                } 
            },
            selectRequerments(index) {
                let item = this.requerments.splice(index,1);
                if(item[0].selected == false) {
                    item[0].selected = true;
                    item[0].class = "filtr__block-btn-active";
                    this.requerments.unshift(item[0]);
                }
                else {
                    item[0].selected = false;
                    item[0].class = "filtr__block-btn";
                    this.requerments.push(item[0]);
                } 
            },
            selectTasks(index) {
                let item = this.tasks.splice(index,1);
                if(item[0].selected == false) {
                    item[0].selected = true;
                    item[0].class = "filtr__block-btn-active";
                    this.tasks.unshift(item[0]);
                }
                else {
                    item[0].selected = false;
                    item[0].class = "filtr__block-btn";
                    this.tasks.push(item[0]);
                } 
            },
            selectExperience(index) {
                let item = this.experience.splice(index,1);
                if(item[0].selected == false) {
                    item[0].selected = true;
                    item[0].class = "filtr__block-btn-active";
                    this.experience.unshift(item[0]);
                }
                else {
                    item[0].selected = false;
                    item[0].class = "filtr__block-btn";
                    this.experience.push(item[0]);
                } 
            }
        },
        watch: {
            display: function() {
                this.show = this.display;
            }
        }
    }
</script>

<style scoped>
    .display {
        display: block;
    }
    h2 {
        margin: 0;
    } 
    .filtr {
        max-width: 820px;
        background-color: #ffffff;
        padding: 25px;
        margin: 15px auto;
        position: relative;
        border-radius: 20px;
    }
    .filtr__block {
        margin-right: 20px;
    }
    .filtr__block-btns {
        margin-top: 15px;
        margin-bottom: 25px;
    }
    .filtr__block-btn {
        padding: 18px 20px;
        background-color: transparent;
        border: 1px solid #ededed;
        cursor: pointer;
        border-radius: 30px;
        margin-right: 10px;
    }
    .filtr__block-btn-active {
        color: #f15a24;
        background-color: #fcded3;
        border: 1px solid #fcded3;
        padding: 18px 20px;
        cursor: pointer;
        border-radius: 30px;
        margin-right: 10px;
    }
    .filtr__block-more {
        padding: 17px 20px;
        background-color: transparent;
        border: 1px solid #36afe4;
        color: #36afe4;
        cursor: pointer;
        border-radius: 30px;
        margin-right: 10px;
    }
    .filtr__block-bottom {
        display: flex;
    }
    .filtr__keys {
        margin-top: 15px;
        border-top: 1px solid #f2f2f2;
        display: flex;
        padding-top: 20px;
        display: none;
    }
    .filtr__key {
        display: flex;
    }
    .filtr__key-item {
        padding: 9px 11px;
        border: 1px solid #f4f4f4;
        border-radius: 8px;
        color: #bfbfbf;
    }
    .filtr__key-item img {
        width: 12px;
        height: 7px;
    }
    .filtr__key-up {
        transform: rotate(180deg);
    }
    .filtr__key-text {
        padding: 9px 11px;
        border: 1px solid transparent;
        border-radius: 8px;
        color: #bfbfbf;
    }
    .filtr__close {
        width: 22px;
        height: 22px;
        position: absolute;
        top: 19px;
        right: 19px;
    }
    .filtr__close button {
        width: 22px;
        height: 22px;
        border: transparent;
        background-color: transparent;
        cursor: pointer;
    }
    .filtr__close button img {
        width: 22px;
        height: 22px;
    }
    .filtr__tool {
        width: 35px;
        height: 13px;
        position: absolute;
        top: -13px;
        left: 50%;
        transform: translateX(-50%);
    }
    .filtr__tool img {
        width: 35px;
        height: 13px;
    }
    .filtr__bottom {
        padding-top: 20px;
        display: flex;
        justify-content: space-between;
    }
    .filtr__info-text {
        color: #29abe2;
        margin-bottom: 7px;
    }
    .filtr__info-subtext {
        color: #7f7f7f;
    }
    .filtr__bottom-clear {
        padding: 17px 35px;
        border: 1px solid #ededed;
        border-radius: 30px;
        background-color: transparent;
        cursor: pointer;
        margin-right: 10px;
        color: #7f7f7f;
    }
    .filtr__bottom-show {
        padding: 18px 70px;
        background-color: #29abe2;
        border: 1px solid #29abe2;
        border-radius: 30px;
        color: #ffffff;
        cursor: pointer;
        font-weight: bold;
    }
</style>