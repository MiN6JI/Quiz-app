<template>
 <!-- eslint-disable -->
    <!-- <div class="text-weight-bold">Hello</div> -->
    <div class="fixed-center" id="main">
        
<!--=======================================================
                    HEADER QUIZ    
    ======================================================= -->
    
    <div class="text-h2">QUIZ
        <q-separator class="q-mb-md" />
    </div>
    
<!--=======================================================
                        Questions Section    
    ======================================================= -->
    
    <div class="shadow-box" v-for="n in 1" :key="n" :class="`shadow-${n}`">
        <div class="text-h6 text-blue-5 q-pa-sm">{{ questions[this.index]['question'] }} </div>

<!--=======================================================
                        Options Section    
    ======================================================= -->

    <div class="row q-ma-lg">
        <div class="col-12">
            <label 
                :for="key" 
                class="q-mt-sm q-pa-sm q-mb-md" 
                id="opt" v-for="opt,key in questions[index]['options']" 
                :class="{'hover:bg-gray cursor-pointer' : selectedAnswer == ''},
                {'bg-blue' : selectedAnswer == key},
                {'bg-green-2' : key == questions[index]['answer'] && selectedAnswer != ''}"
                >
                <input type="radio" :id="key" class="hidden" :value="key" @change="ans($event)" :disabled="selectedAnswer != '' " /> {{ opt }}
            </label>
            <div class="q-mt-sm">

                <button 
                class="float-right bg-primary text-white text-h6 rounded-borders no-border q-px-sm q-mx-md q-my-lg" v-show="selectedAnswer != ''"
                @click="nextQuestion"
                >
                Next >
                </button>

                <button 
                class="float-right bg-primary text-white text-h6 rounded-borders no-border q-px-sm q-mx-md q-my-lg" v-show="selectedAnswer != '' && index < count"
                @click="showResult"
                >
                Finish >

                </button>
            </div>
        </div>
        
    </div>
    

    </div>
        
    </div>
</template>

<script>
// eslint-disable-next-line
import { count } from 'console'
import { ref } from 'vue'

    export default {
        name: 'Quiz-app',

    // =======================================================
    // Real Questions Section    
    // ======================================================= 
    data(){
        return{
            selectedAnswer: '',
            index: 0,
            count: 3,
            questions: [
                {
                    question: "Chlorofluorocarbons are accountable for which of the following process?",
                    options: {a: 'Ozone depletion', b: 'Acid rain', c: 'Soil pollution', d: 'Genetic mutation'},
                    answer: 'a'
                },
                {
                    question: "Which of the following gases is responsible for bleaching of plants?",
                    options: {a: 'NO2', b: 'SO3', c: 'SO2', d: 'CO2'},
                    answer: 'c'
                },
                {
                    question: "Which of the following modes of transport should we opt for as far as possible in order to do our bit to protect the environment?",
                    options: {a: ' Taxis', b: 'Public transport', c: 'Private transport', d: 'Own car'},
                    answer: 'b'
                },
            ]
        }
    },

    methods: {
        ans(e) {
            this.selectedAnswer = console.log(e.target.value)
            console.log(this.selectedAnswer)
        },
        nextQuestion(){
        this.index++
        this.selectedAnswer = ''
        },
        showResult(){
            this.index++
        }
    }

    }
</script>

<style scoped>
/* eslint-disable-next-line */
#main{
    width: 700px;
}

#opt{
    display: block;
    width: 100%;
    border: 1px solid #b9b9b9;
    border-radius: 5px;
}
/* #opt:hover{
    background-color: #f3f3f3;
} */
</style>