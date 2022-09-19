<template>
    <div class="box">
        <div class="frames-show">
            <div class="tip-amount">
                <h3 class="tip-title">Tip Amount <br> <span>/ person</span> </h3>
                <h3 class="tip-money">${{tipAmount}}</h3>
            </div>
            <div class="total">
                <h3 class="tip-title">Total <br> <span>/person</span> </h3>
                <h3 class="tip-money">${{total}}</h3>
            </div>
            <button type="reset" class="reset-btn" v-on:click="resetData($event)">RESET</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'show-bill',
    props: {
        tipAmount: {type: Number, default: Number(0)},
        total: {type: Number, default: Number(0)}
    },
    data() {
        return {

        }
    },
    methods: {
        resetData(e) {
            this.$emit('resetData');
        }
    }
}
</script>

<style>
.box {
    width: 50%;
}

.frames-show{
    height: 85%;
    width: 90%;
    margin: 25px auto;
    border-radius: 20px;
    background-color: #00474A;
}
.tip-amount, .total{
    display: flex;
    width: 100%;
    margin: 5px auto;
}
.tip-title, .tip-money{
    width: 100%;
    margin-top: 30px;
    display: inline;
}

.tip-money{
    font-size: 30px;
    font-weight: 700;
    text-align: right;
    color: #27CCB3;
    padding-right: 5px;
}

.tip-title{
    color: #EBFDFF;
    padding-left: 10px;
}

.tip-title span{
    font-size: medium;
    color: #719EA3;
}
.reset-btn{
    width: 80%;
    margin: 50px 34px 10px 34px;
    height: 40px;
    background-color: #26C2AE;
    color: #004840;
    border-radius: 5px;
    cursor: pointer;
    font-size: large;
    font-weight: 700;
    border: none;
}
.reset-btn:hover{
    background-color: #9EE8E0;
    color: #004041;
}
</style>

<style>
@media only screen and (max-width: 1440px) {
    .tip-money{
        padding-left: 40px;
        font-size: 30px;
    }
    
    .tip-title{
        padding-top: 7px;
        font-size: 16px;
    }
    .reset-btn{
        font-size: 16px;
    }
}

/* Big tablet to 1200px; */
@media only screen and (max-width:1200px) {
    .tip-money{
        font-size: 20px;
        padding-right: 5px;
    }
    
    .tip-title{
        padding-top: 0px;
        font-size: 12px;
    }
    .tip-title span{
        font-size: 12px;
    }
    .reset-btn{
        font-size: 14px;
        margin: 90px 27px 10px 27px;
        height: 35px;
    }
}

/* Small tablet to big tablet from 768x to 1023px */
@media only screen and (max-width:1023px){
    .container{
        flex-direction: column;
        height: 670px;
        top: 50px;
    }
    .frames-bill {
        width: 100%; 
        margin-left: 0px
    }
    .box{
        width: 100%;
        position: absolute;
        top: 350px;
    }
    .frames-bill-child{
        width: 380px;
    }
    .money {
        font-size: 20px;
        padding-top: 2px;
        padding-right: 5px;
    } 
    .select-tip {
        width: 380px;
    }
    .select-tip-btn,
    .select-tip-btn-input{
        font-size: 16px;
    }
    .frames-bill-child-person{
        width: 55%;
    }
    .btn-calculator {
        width: 27%;
        left: 275px;
    }
    .tip-money{
        font-size: 30px;
        padding-right: 5px;
    }
    
    .tip-title{
        padding-top: 3px;
        padding-left: 20px;
        font-size: 16px;
        width: 60%;
    }
    .tip-title span{
        font-size: 10px;
    }
    .reset-btn{
        font-size: 14px;
        margin: 60px 33px 30px 33px;
        height: 35px;
    }
}

@media only screen and (max-width: 780px){
    
    .container{
        flex-direction: column;
        height: 670px;
        top: 50px;
    }
    .frames-bill {
        width: 100%; 
        margin-left: 0px
    }
    .box{
        width: 100%;
        position: absolute;
        top: 350px;
    }
    .frames-bill-child{
        width: 340px;
    }
    .money {
        font-size: 20px;
        padding-top: 7px;
        padding-right: 5px;
    } 
    .select-tip {
        width: 340px;
    }
    .select-tip-btn,
    .select-tip-btn-input{
        font-size: 16px;
    }
    .frames-bill-child-person{
        width: 59%;
    }
    .btn-calculator {
        width: 28%;
        left: 250px;
    }
    .tip-money{
        font-size: 30px;
        padding-right: 5px;
    }
    
    .tip-title{
        padding-top: 3px;
        padding-left: 20px;
        font-size: 16px;
        width: 60%;
    }
    .tip-title span{
        font-size: 10px;
    }
    .reset-btn{
        font-size: 14px;
        margin: 60px 33px 30px 33px;
        height: 35px;
    }
}

/* Small phones to small tablets */
@media only screen and (max-width: 767px){
    
    .container{
        flex-direction: column;
        height: 630px;
        top: 50px;
    }
    .frames-bill {
        width: 100%; 
        margin-left: 0px
    }
    .box{
        width: 100%;
        position: absolute;
        top: 350px;
    }
    .frames-bill-child{
        width: 270px;
    }
    .money {
        font-size: 20px;
        padding-top: 7px;
    } 
    .icon-dollar{
        width: 70%;
    }
    .select-tip {
        width: 270px;
    }
    .select-tip-btn,
    .select-tip-btn-input{
        font-size: 14px;
    }
    .frames-bill-child-person{
        width: 57%;
    }
    .btn-calculator {
        width: 28%;
        left: 200px;
    }
    .tip-money{
        font-size: 18px;
    }
    
    .tip-title{
        padding-top: 2px;
        font-size: 10px;
        width: 100%;
    }
    .tip-title span{
        font-size: 10px;
    }
    .reset-btn{
        font-size: 14px;
        margin: 30px 28px 30px 28px;
        height: 35px;
    }
}
 

/* Small phones from 0 to 480px; */
@media only screen and (max-width: 480px){
    .container{
        flex-direction: column;
        height: 620px;
        top: 50px;
    }
    .frames-bill {
        width: 100%; 
        margin-left: 0px
    }
    .box{
        width: 100%;
        position: absolute;
        top: 350px;
    }
    .frames-bill-child{
        width: 170px;
    }
    .money {
        font-size: 16px;
        padding-top: 5px;
    } 
    .select-tip {
        width: 170px;
    }
    .select-tip-btn,
    .select-tip-btn-input{
        font-size: 14px;
    }
    .frames-bill-child-person{
        width: 50%;
    }
    .btn-calculator {
        width: 25%;
        left: 135px;
    }
    .person {
        padding-top: 7px;
        font-size: 18px;
        width: 13%;
    } 
    .tip-money{
        padding-left: 10px;
        font-size: 15px;
    }
    
    .tip-title{
        padding-top: 3px;
        font-size: 10px;
    }
    .tip-title span{
        font-size: 8px;
    }
    .reset-btn{
        font-size: 14px;
        margin: 30px 16px 10 16px;
        height: 35px;
        padding-top: 5px;
    }
}
</style>