<template>
    <div class="hello">
        <h2>{{ myDate }}</h2>
        <h1>{{ myTime }}</h1>
    </div>
</template>

<script>
    export default {
        name: 'Timer',
        methods: {

            zeroPadding: function(num, digit){
                var zero = '';
                for(var i = 0; i < digit; i++) {
                    zero += '0';
                }
                return (zero + num).slice(-digit);
            },
            clock: function () {
                setInterval(() => {
                    // Get real time
                    let time = new Date();
                    this.myTime = this.zeroPadding(time.getHours(), 2) + ':' + this.zeroPadding(time.getMinutes(), 2) + ':' + this.zeroPadding(time.getSeconds(), 2);
                    //console.log(this.myTime)
                }, 1000);
            },
            baret: function(){
                setInterval(() => {
                let today = new Date();
                let week = ['Niedziela', 'Poniedziałek', 'Wtorek', 'Środa', 'Czwartek', 'Piątek', 'Sobota'];
                this.myDate = this.zeroPadding(today.getFullYear(), 4) + '-' + this.zeroPadding(today.getMonth()+1, 2) + '-' + this.zeroPadding(today.getDate(), 2) + ' ' + week[today.getDay()];
                //console.log(this.myDate)
                }, 1000);
            }

        },
        data(){
            return{
                myTime:"",
                myDate:"",

            }
        },
        mounted() {
            this.myDate = this.baret();
            this.myTime = this.clock();
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    h1{
        font-size:120px;
        margin:0;
        padding:0;
    }
    h2{
        padding:0;
        margin:0;

    }
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }
</style>
