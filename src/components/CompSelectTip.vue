<template>
  <div class="frames-selcect-tip">
    <label for="tip">Seclet Tip %</label>
    <div class="select-tip row">
        <button class="select-tip col-sm-3">30%</button>
        <button class="select-tip col-sm-3">30%</button>
        <button class="select-tip col-sm-3">30%</button>
        <button class="select-tip col-sm-3">30%</button>
        <button class="select-tip col-sm-3">30%</button>
        <button class="select-tip col-sm-3">30%</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'select-tip',
    data() {
        return {

        }
    },
    methods: {

    }
}
</script>

<style>
label {
    margin-left: 15px;
    color: #869294;
    font-weight: 500;
}
.select-tip{
    width: 100%;
    margin-left: 4px;
}
</style>