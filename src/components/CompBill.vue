<template>
    <div class="frames-bill">
        <span class="label-bill">Bill</span>
        <div class="frames-bill-child">
            <i class="icon-dollar">
                <svg xmlns="http://www.w3.org/2000/svg" width="11" height="17">
                    <path fill="#9EBBBD"
                        d="M6.016 16.328v-1.464c1.232-.08 2.22-.444 2.964-1.092.744-.648 1.116-1.508 1.116-2.58v-.144c0-.992-.348-1.772-1.044-2.34-.696-.568-1.708-.932-3.036-1.092V4.184c.56.144 1.012.4 1.356.768.344.368.516.816.516 1.344v.288h1.824v-.432c0-.448-.088-.876-.264-1.284a3.783 3.783 0 00-.744-1.116A4.251 4.251 0 007.54 2.9a5.324 5.324 0 00-1.524-.492V.872H4.288V2.36a5.532 5.532 0 00-1.416.324c-.448.168-.84.392-1.176.672-.336.28-.604.616-.804 1.008-.2.392-.3.844-.3 1.356v.144c0 .96.316 1.708.948 2.244.632.536 1.548.884 2.748 1.044v3.912c-.704-.16-1.248-.472-1.632-.936-.384-.464-.576-1.08-.576-1.848v-.288H.256v.576c0 .464.08.924.24 1.38.16.456.404.88.732 1.272.328.392.744.728 1.248 1.008s1.108.476 1.812.588v1.512h1.728zM4.288 7.424c-.688-.128-1.164-.332-1.428-.612-.264-.28-.396-.644-.396-1.092 0-.464.176-.832.528-1.104.352-.272.784-.448 1.296-.528v3.336zm1.728 5.712V9.344c.768.128 1.328.328 1.68.6.352.272.528.688.528 1.248 0 .544-.196.984-.588 1.32-.392.336-.932.544-1.62.624z" />
                </svg>
            </i>
            <input type="number" class="money" placeholder="0" id="inputMoney" v-on:keyup="inputMoney($event)" min="0">
        </div>
        <div class="frames-selcect-tip">
            <span class="label-select-tip">Seclet Tip ({{ chpercents }}%)</span>
            <div class="select-tip">
                <button class="select-tip-btn" v-for="(percent, index) in percents" v-bind:key="index"
                    v-bind:value="percent" v-on:click="selectTip($event)">{{ percent }}%</button>
                <input class="select-tip-btn-input" placeholder="Custom" type="number" max="100" min="0"
                    v-on:keyup="inputTip($event)" id="inputTip">
            </div>
        </div>
        <span class="label-person">Person of number</span>
        <div class="box-calculator">
            <div class="frames-bill-child-person">
                <i class="icon-person">
                    <svg xmlns="http://www.w3.org/2000/svg" width="13" height="16">
                        <path fill="#9EBBBD"
                            d="M9.573 7.729c.406 0 .784.07 1.126.209.342.14.639.33.881.569.232.227.438.503.614.82a5.1 5.1 0 01.407.949c.097.312.178.654.242 1.016.062.359.105.699.126 1.011.02.307.031.624.031.945 0 .836-.259 1.512-.768 2.01-.504.492-1.17.742-1.98.742H2.748c-.81 0-1.477-.25-1.98-.742C.259 14.76 0 14.084 0 13.248c0-.322.01-.64.032-.945.02-.312.063-.652.126-1.01.063-.363.144-.705.242-1.017.1-.323.238-.643.407-.948.176-.318.382-.594.613-.821.243-.238.54-.43.882-.57.342-.138.72-.208 1.125-.208.16 0 .313.067.61.265.183.123.397.264.636.421.204.134.48.259.822.372.333.11.671.167 1.005.167a3.19 3.19 0 001.006-.167c.341-.113.618-.238.822-.372l.636-.42c.296-.2.45-.266.61-.266zM6.598 0C7.63 0 8.522.38 9.252 1.129s1.1 1.666 1.1 2.724c0 1.06-.37 1.976-1.1 2.725-.73.75-1.623 1.13-2.654 1.13-1.03 0-1.924-.38-2.653-1.13-.73-.749-1.1-1.666-1.1-2.725 0-1.058.37-1.975 1.1-2.724C4.675.379 5.567 0 6.598 0z" />
                    </svg>
                </i>
                <div class="person">{{ persons }}</div>
            </div>
            <button class="btn-calculator" v-on:click="calculate()">CAL</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'bill',
    props: {
        persons: { type: Number, default: Number(0) },
        chpercents: { type: Number, default: Number(0) },
    },
    data() {
        return {
            percents: [5, 10, 15, 25, 50],
        }
    },
    methods: {
        selectTip(e) {
            const per = Number(e.target.value);
            this.$emit('selectPercents', per)

        },
        inputMoney(e) {
            if (e.target.value < 0) {
                alert('Money must larger than zero.')
            }
            else {
                const money = Number(e.target.value);
                    this.$emit('inputMoney', money);
            }
        },
        inputTip(e) {
            if (e.target.value > 100 || e.target.value < 0) {
                alert('percent must be larger than zero percent and less than one hundred percents.')
            }
            else {
                const per = Number(e.target.value);
                this.$emit('selectPercents', per);
            }
        },
        calculate()
        {
            this.$emit('calculate')
        }
    }
}
</script>

<style>
.frames-bill {
    width: 50%;
    position: relative;
}

.frames-bill-child {
    border: 3px solid #333;
    border-radius: 5px;
    width: 350px;
    height: 40px;
    display: flex;
    position: absolute;
    top: 47px;
    left: 20px;
}

.frames-bill-child:hover,
.frames-bill-child-person:hover {
    border-color: #56A79C;
    cursor: pointer;
}

.label-bill {
    margin-left: 15px;
    color: #869294;
    font-weight: 500;
    position: absolute;
    top: 25px;
    left: 10px;
}

.icon-dollar {
    padding-left: 15px;
    padding-top: 8px;
    width: 100%;
}

.money {
    cursor: text;
    margin: 0px;
    width: 70%;
    text-align: right;
    border: none;
    background-color: none;
    font-weight: 700;
    padding-top: 5px;
    font-size: 20px;
    outline: none;
}

.money:focus {
    border-color: none;
}

.label-select-tip {
    color: #869294;
    font-weight: 500;
    position: absolute;
    top: 120px;
    left: 22px;
    position: relative;
}

.select-tip {
    margin-left: 4px;
    display: flex;
    position: absolute;
    top: 150px;
    left: 15px;
    flex-wrap: wrap;
    width: 350px;
}

.select-tip-btn {
    width: 32%;
    margin: 3px auto;
    height: 40px;
    border-radius: 3px;
    font-size: large;
    cursor: pointer;
    background-color: #00474A;
    color: #CDF8FA;
    font-weight: 600;
    border: none;
}

.select-tip-btn-input {
    cursor: text;
    width: 32%;
    margin: 3px auto;
    height: 40px;
    border-radius: 3px;
    font-size: large;
    text-align: right;
}

.select-tip-btn:hover {
    background-color: #26C2AE;
    color: #13686A;
    transition-duration: 0.2s;
}

.select-tip-btn:focus {
    background-color: #28C1AD;
    color: #004545;
}

.frames-bill-child-person {
    border: 3px solid #333;
    border-radius: 5px;
    /* width: 350px; */
    height: 40px;
    display: flex;
    position: absolute;
    top: 280px;
    left: 20px;
    width: 58%;
}

.btn-calculator {
    width: 30%;
    font-size: 16px;
    font-weight: 700;
    border: none;
    cursor: pointer;
    background-color: #26C2AE;
    color: #004840;
    border-radius: 5px;
    height: 40px;
    position: absolute;
    top: 280px;
    left: 250px;
}

.btn-calculator:hover{
    background-color: #9EE8E0;
    color: #004041;
}

.box-calculator {
    display: flex;
}

.label-person {
    margin-left: 15px;
    color: #869294;
    font-weight: 500;
    position: absolute;
    top: 255px;
    left: 10px;
}

.icon-person {
    padding-left: 15px;
    padding-top: 10px;
    width: 100%;
}

.person {
    padding-top: 5px;
    font-size: 23px;
    font-weight: 500;
    text-align: right;
    padding-right: 15px;
}
</style>

<style>
@media only screen and (max-width: 1440px) {
    .frames-bill-child {
        width: 280px;
    }

    .money {
        font-size: 20px;
        padding-right: 5px;
    }

    .select-tip {
        width: 280px;
    }

    .select-tip-btn,
    .select-tip-btn-input {
        font-size: 16px;
    }
    .btn-calculator {
    left: 205px;
    }
}

/* Big tablet to 1200px; */
@media only screen and (max-width:1200px) {
    .frames-bill-child {
        width: 240px;
    }

    .money {
        font-size: 20px;
        padding-top: 7px;
    }

    .select-tip {
        width: 240px;
    }

    .select-tip-btn,
    .select-tip-btn-input {
        font-size: 14px;
    }
    .btn-calculator {
        width: 26%;
        left: 185px;
    }
}

/* Small tablet to big tablet from 768x to 1023px */
@media only screen and (max-width:1023px) {
    .container {
        flex-direction: column;
        height: 670px;
        top: 50px;
    }

    .frames-bill {
        width: 100%;
        margin-left: 0px
    }

    .box {
        width: 100%;
        position: absolute;
        top: 350px;
    }

    .frames-bill-child {
        width: 380px;
    }

    .money {
        font-size: 20px;
        padding-top: 5px;
        padding-right: 5px;
    }

    .select-tip {
        width: 380px;
    }

    .select-tip-btn,
    .select-tip-btn-input {
        font-size: 16px;
    }

    .tip-money {
        font-size: 30px;
        padding-right: 5px;
    }

    .tip-title {
        padding-top: 3px;
        padding-left: 20px;
        font-size: 16px;
        width: 60%;
    }

    .tip-title span {
        font-size: 10px;
    }

    .reset-btn {
        font-size: 14px;
        margin: 60px 33px 30px 33px;
        height: 35px;
    }
}

@media only screen and (max-width: 780px) {

    .container {
        flex-direction: column;
        height: 670px;
        top: 50px;
    }

    .frames-bill {
        width: 100%;
        margin-left: 0px
    }

    .box {
        width: 100%;
        position: absolute;
        top: 350px;
    }

    .frames-bill-child {
        width: 340px;
    }

    .money {
        font-size: 20px;
        padding-top: 5px;
        padding-right: 5px;
    }

    .select-tip {
        width: 340px;
    }

    .select-tip-btn,
    .select-tip-btn-input {
        font-size: 16px;
    }

    .frames-bill-child-person {
        width: 340px;
    }

    .tip-money {
        font-size: 30px;
        padding-right: 5px;
    }

    .tip-title {
        padding-top: 3px;
        padding-left: 20px;
        font-size: 16px;
        width: 60%;
    }

    .tip-title span {
        font-size: 10px;
    }

    .reset-btn {
        font-size: 14px;
        margin: 60px 33px 30px 33px;
        height: 35px;
    }
}

/* Small phones to small tablets */
@media only screen and (max-width: 767px) {

    .container {
        flex-direction: column;
        height: 630px;
        top: 50px;
    }

    .frames-bill {
        width: 100%;
        margin-left: 0px
    }

    .box {
        width: 100%;
        position: absolute;
        top: 350px;
    }

    .frames-bill-child {
        width: 270px;
    }

    .money {
        font-size: 20px;
        padding-top: 7px;
    }

    .icon-dollar {
        width: 70%;
    }

    .select-tip {
        width: 270px;
    }

    .select-tip-btn,
    .select-tip-btn-input {
        font-size: 14px;
    }

    .frames-bill-child-person {
        width: 270px;
    }
}

@media screen and (max-width:500px) {
    .container {
        flex-direction: column;
        height: 630px;
        top: 50px;
    }

    .frames-bill {
        width: 100%;
        margin-left: 0px
    }

    .box {
        width: 100%;
        position: absolute;
        top: 350px;
    }

    .frames-bill-child {
        width: 210px;
    }

    .money {
        font-size: 18px;
        padding-top: 5px;
    }

    .icon-dollar {
        width: 70%;
    }

    .select-tip {
        width: 210px;
    }

    .select-tip-btn,
    .select-tip-btn-input {
        font-size: 14px;
    }

    .frames-bill-child-person {
        width: 210px;
    }

    .tip-money {
        font-size: 22px;
    }

    .tip-title {
        padding-top: 2px;
        padding-left: 20px;
        font-size: 12px;
    }

    .tip-title span {
        font-size: 8px;
    }

    .reset-btn {
        font-size: 14px;
        margin: 30px 23px 30px 23px;
        height: 35px;
    }
}
</style>