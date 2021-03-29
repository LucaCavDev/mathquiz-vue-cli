<template>
  <div class="mathquiz" id="mathquiz">

    <h1>Meth Quiz XD</h1>
    <OperatorQuiz @onBack="clearOperator" v-if="operator" :operator="operator"/>
    <!-- <h2>Operator in use: {{operator}}</h2> -->
    <OperatorSelector v-if="!operator" @changeOperator="changeOperator"/>

  </div>
</template>

<script>
import OperatorSelector from "@/components/OperatorSelector.vue";
import OperatorQuiz from "@/components/OperatorQuiz.vue";


export default {

    name: "MathQuiz",

    data () {
        return {
            operator: null,
        }
    },

    methods: {
        changeOperator(operator) {
            console.log(operator);
            this.operator = operator;
        },
        clearOperator(){
            this.operator = null;
        },
    },
  components: {
    OperatorSelector,
    OperatorQuiz,
  },


};
</script>

<style lang="scss">
    button {
        margin: 10px;
        width: 180px;
    }

</style>