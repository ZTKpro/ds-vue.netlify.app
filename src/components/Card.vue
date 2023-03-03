<template>
    <div :class="['card', suit]">
        <div class="card-header">{{ convertSymbols(suit) }}</div>
        <div class="card-body">
            <div class="card-value">{{ value }}</div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        suit: {
            type: String,
            required: true
        },
        value: {
            type: String,
            required: true
        }
    },
    methods: {
        convertSymbols: function (symbol) {
            if("PIK" === symbol) {
                return "♠"
            } else if("TRE" === symbol) {
                return "♥"
            } else if("KAR" === symbol) {
                return "♦"
            } else if("KIE" === symbol) {
                return "♣"
            } else {
                return symbol
            }
        }
    }
}
</script>

<style>
.card {
    margin: 20px;
    display: inline-block;
    width: 100px;
    height: 150px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
    text-align: center;
    font-size: 24px;
}

.card-header {
    padding: 10px;
    font-weight: bold;
    font-size: 30px;
}

.card-body {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
}

.card-value {
    margin-top: 10px;
}

.card.PIK {
    color: #fff;
}

.card.TRE {
    color: #fff;
}

.card.KAR {
    color: red;
}

.card.KIE {
    color: red;
}
</style>
