<template>
    <div class="duel" v-bind:class='{fond: active}'>
        <header>
            <img id='logo' src="./../assets/logo.svg">
            <img id='menu' src="./../assets/menu.svg">
            <hr>
        </header>
        <article>
            <div  @click='calculer' class="calcul" v-bind:class="{play2: isActive}">{{ calcul }}</div>
        </article>
        <div class="board">
            <div class="touche" v-for="n in 10" @click="afficher(n - 1)">
                {{ n - 1 }}
            </div>
            <div class="touche" @click="moins">
                -
            </div>
            <div class="touche" @click="supprimer">
                C
            </div>
        </div>
        <article>
            <div class="resultat" v-bind:class='{resultFaux: activeFaux, resultVrai: activeVrai}'>{{ inserer }}</div>
            <img v-bind:class='{imgPlay: active}' @click='valider' id='play' src="./../assets/play.svg">
        </article>
    </div>

</template>

<script>
export default {
    name: 'Duel',
    data: function() {
        return {
            isActive: true,
            inserer: '',
            calcul: 'PLAY',
            calculA: null,
            calculB: null,
            operateur: ['+', '-', '*'],
            compteur: 0,
            resultat: null,
            active: false,
            activeVrai: false,
            activeFaux: false,
        }
    },
    methods: {
        //fonction permettant d'afficher le nombre clické
        afficher: function(v){
            this.inserer += v ;
        },
        //fonction permettant de supprimer le nombre dernier nombre clické
        supprimer: function(){
            const a = this.inserer.substring(0, this.inserer.length-1);
            this.inserer = a;
        },
            //fonction permettant de mettre un moins devant le resultat
        moins: function(){
            if(this.inserer === ''){
                this.inserer = '-';
            }
        },
        //fonction permettant de calculer le resultat du calcul et de le comparer
        //au resultat de l'user
        valider: function(){
            const temp = null;
            if (this.calcul.indexOf('+') !== -1) {
                this.resultat = this.calculA + this.calculB;
            }else if (this.calcul.indexOf('-') !== -1) {
                this.resultat = this.calculA - this.calculB;
            }else if (this.calcul.indexOf('*') !== -1) {
                this.resultat = this.calculA * this.calculB;
            }

            if (this.resultat !== null) {
                const a = this;
                if (this.resultat == this.inserer) {
                        this.activeVrai = true;
                        this.active = true;


                }else{
                this.activeFaux = true;
                this.active = true;

                }
                const timeoutID = window.setTimeout( function(){
                    a.isActive = true;
                    a.calcul = 'PLAY';
                    a.activeFaux = false;
                    a.activeVrai = false;
                    a.active = false;

                }, 5000);
            }



        },
        calculer: function(){
            this.isActive = false;
            this.calculA = Math.floor(Math.random() * (20 - 0)) + 0;
            this.calculB = Math.floor(Math.random() * (20 - 0)) + 0;
            const temp = Math.floor(Math.random() * (3 - 0)) + 0;
            this.calcul = this.calculA + this.operateur[temp]+this.calculB;
        },
    },
}
</script>

<style scoped>
#menu{
    position: absolute;
    width: 60px;
    height: 60px;
    right: 20px;
    top: 22px;
}
#logo{
    width: 100px;
    height: 100px;
    position: absolute;
    top: 0;
}
.board {
    display: grid;
    grid-template-columns: repeat(4, 60px);
    grid-template-rows: repeat(4, 60px);
    position: absolute;
    top: 280px;
    left: 50px;

}
.touche {
    color: #fff;
    border: 3px solid #E41D1A;
    background: #44A5A5;
    border-radius: 10px;
    font-size: 2em;
    margin: 1px;
    text-align: center;
}


hr{
    height: 10px;
    background: #44A5A5;
    color: #44A5A5;
    position: relative;
    top: 80px;
}
.calcul{
    width: 70vw;
    height: 100px;
    background-color: black;
    border-radius: 20px;
    position: absolute;
    top: 150px;
    left: 50px;
    color: #fff;
    font-size: 2em;
    text-align: center;
    line-height: 100px;
}
.play2{
    background: url('./../assets/play2.svg') black 80px 10px no-repeat;
    background-size: 80px;
}

.resultat{
    width: 70vw;
    height: 100px;
    background: lightblue;
    border-radius: 20px;
    position: absolute;
    top: 500px;
    left: 50px;
    text-align: center;
    font-size: 2em;
    color: #fff;
    line-height: 100px;
}
#play{
    width: 80px;
    height: 80px;
    position: absolute;
    top: 510px;
    right: 20px;
}
.resultVrai{
    background: url('./../assets/happy.svg') PaleGreen 170px 20px no-repeat;
    background-size: 70px;
}
.resultFaux{
    background: url('./../assets/angry.svg') Salmon 170px 20px no-repeat;
    background-size: 70px;
}
.imgPlay{
    visibility: hidden;
}

</style>
