<template>
    <div id="app">
        <div class="container">
            <CompBill
                v-bind:persons = "persons"
                v-bind:chpercents="chpercents"
                v-on:selectPercents = "selectPercents"
                v-on:inputMoney = "inputMoney"
                v-on:calculate = "calculate"
            />

            <Show
                v-on:resetData = "resetData"
                v-bind:tipAmount="tipAmount"
                v-bind:total="total"
            />

        </div>
    </div>
</template>

<script>
import CompBill from './components/CompBill.vue'
import Show from './components/show.vue';
export default {
    name: "app",
    data() {
        return {
            money: 0,
            tipAmount: 0,
            total: 0,
            persons: 0,
            chpercents: 0,
        };
    },
    components: { 
        CompBill, Show 
    },
    methods: {
        resetData()
        {
            this.money = 0;
            this.tipAmount = 0;
            this.total = 0;
            this.persons = 0;
            document.getElementById('inputMoney').value = "";
            document.getElementById('inputTip').value = "";
            this.chpercents = 0;
        },
        selectPercents(per)
        {
            this.chpercents = per;
        },
        inputMoney(ipmoney)
        {
            this.money = ipmoney;
        },
        calculate()
        {
            this.tipAmount = Number((this.money * (this.chpercents / 100)).toFixed(2));
            this.total = Number((this.total + this.tipAmount).toFixed(2));
            this.persons += 1;
        }
    }
}
</script>
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: #C5E5E7;
}

.container {
    background-color: #FFF;
    height: 50%;
    width: 50%;
    position: absolute;
    top: 25%;
    left: 25%;
    border-radius: 20px;
    display: flex;
}
</style>
