<template>
    <div class="container-fluid">
        <!-- <h1> {{operator}}</h1> -->
        <div v-if="isQuizStarted">
            <h4>{{operandLeft}} {{operator}} {{operandRight}}</h4>
            
            <button @click="selectAnswer(answer)"
                    v-for="(answer, index) of answers"
                    :key="index"
                    class="btn btn-info"
            > 
                {{answer}}
            </button>


        </div>

        <div v-if="!isQuizStarted">
            <button @click="startQuiz" class="btn btn-danger">Start</button>
        </div>

        <button @click="$emit('onBack')" class="btn btn-primary">Back</button>

    </div>

  
</template>

<script>
export default {
    props: ["operator"],
    data () {
        return {
            isQuizStarted: false,
            operandLeft: null,
            operandRight: null,
            answers: [],
            expectedAnswer: null
        };

    },
    methods: {
        selectAnswer(answerSelected) {
            if (answerSelected !== this.expectedAnswer) {
                alert("WRONG ANSWER");
            }
            // alert("GOOD RESTART QUIZ!")
            this.startQuiz();
        },
        startQuiz () {
            this.isQuizStarted = true;
            this.operandLeft = parseInt(Math.random() * 13);
            this.operandRight = parseInt(Math.random() * 13);

            const methods = {
                "+": (a, b) => a + b,
                "-": (a, b) => a - b,
                "/": (a, b) => a / b,
                "*": (a, b) => a * b
            };
/*
            const methodToUse = methods[this.operator];

            this.answers = [];
        
            this.answers.push(methodToUse(this.operandLeft, this.operandRight + 1));
            this.answers.push(methodToUse(this.operandLeft + 1, this.operandRight));
            this.answers.push(methodToUse(this.operandLeft - 1, this.operandRight));
            this.answers.push(methodToUse(this.operandLeft, this.operandRight - 1));
            this.answers.push(methodToUse(this.operandLeft - 1, this.operandRight - 1));
            this.answers.push(methodToUse(this.operandLeft + 1, this.operandRight + 1));



            const expectedAnswer = methodToUse(this.operandLeft, this.operandRight);

            this.answers[ parseInt(Math.random() * this.answers.length) ] = expectedAnswer;

            this.expectedAnswer = expectedAnswer;

            */

          // var randomNumber = Math.floor((Math.random() * 10) + 1);
        


            const methodToUse = methods[this.operator];

            this.answers = [];

            var arr = [];
            while(arr.length < 4){
                var r = Math.floor(Math.random() * 4) + 1;
                if(arr.indexOf(r) === -1) arr.push(r);
            }
            console.log(arr);


            // function Random1() {
            //     return Math.floor((Math.random() * 5) + 1);
            // }
            // function Random2() {
            //     return Math.floor((Math.random() * 5) + 1);
            // }
            // function Random3() {
            //     return Math.floor((Math.random() * 5) + 1);
            // }
            // function Random4() {
            //     return Math.floor((Math.random() * 5) + 1);
            // }



            // this.answers.push(methodToUse(this.operandLeft, this.operandRight + Random1()));
            // this.answers.push(methodToUse(this.operandLeft + Random2(), this.operandRight));
            // this.answers.push(methodToUse(this.operandLeft, this.operandRight - Random3()));
            // this.answers.push(methodToUse(this.operandLeft - Random4(), this.operandRight));

            this.answers.push(methodToUse(this.operandLeft, this.operandRight + arr[0]));
            this.answers.push(methodToUse(this.operandLeft + arr[1], this.operandRight));
            this.answers.push(methodToUse(this.operandLeft, this.operandRight - arr[2]));
            this.answers.push(methodToUse(this.operandLeft - arr[3], this.operandRight));






            const expectedAnswer = methodToUse(this.operandLeft, this.operandRight);

            this.answers[ parseInt(Math.random() * this.answers.length) ] = expectedAnswer;

            this.expectedAnswer = expectedAnswer;
        }
    }

};
</script>

<style scoped lang="scss">


</style>