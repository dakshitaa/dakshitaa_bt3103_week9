<template>
<div>
    <h2>Menu</h2>
    <ul>
        <li v-for='item in itemsSelected' :key='item.id'>
            {{item[0]}} x {{item[1]}}
        </li>
    </ul>
    <button id='total-button' v-on:click="findSubTotal(); findGrandTotal(); toggleShowTotal()">Calculate Total</button>
    <div id='total' v-show='showTotal'>
        <br>
        Subtotal: ${{subTotal}}<br><br>
        Grand Total: ${{grandTotal}}</div>
</div>
    
</template>

<script>
export default {
    props: {
        itemsSelected: {
              type: Array
        }
    },

    data() {
        return {
            subTotal: 0,
            grandTotal: 0,
            showTotal: false
        }
    },

    methods: {
        findSubTotal: function() {
            var i;
            this.subTotal = 0;
            for (i=0 ; i < this.itemsSelected.length ; i++) {
                this.subTotal += this.itemsSelected[i][2] * this.itemsSelected[i][1];
            }
            this.subTotal = (this.subTotal).toFixed(2);
        },

        findGrandTotal: function() {
            this.grandTotal = (this.subTotal * 1.07).toFixed(2);
        },

        toggleShowTotal: function() {
            this.showTotal = true
        }
    }

}
</script>

<style scoped>

#total-button {
  height: 45px;
  width: 175px;
  border-radius: 5px;
  font-size: 20px;
}

li {
    margin: 20px 0;
}

#total {
    margin-top: 10px;
}
</style>