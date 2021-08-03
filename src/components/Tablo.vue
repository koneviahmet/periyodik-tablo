<template>
    <div class="container">
      <div class="footer">
        <div class="menu">
          <div class="menu-ust">Üst Menü</div>
          <div class="menu-alt">
              <div 
                v-for="(g, key) in ['1A','2A','3B','4B','5B','6B','7B','8B','8B','8B','1B','2B','3A','4A','5A','6A','7A','8A']" 
                :key="key" @click="setGrupColor(g)">
                  {{g}} Grubu
              </div>
          </div>
        </div>
      </div>

      <div class="center">
        
        
        <div class="left">
            <div class="periyot_adi" @click="setPeriyotColor(1)">1. Periyot</div>
            <div class="periyot_adi" @click="setPeriyotColor(2)">2. Periyot</div>
            <div class="periyot_adi" @click="setPeriyotColor(3)">3. Periyot</div>
            <div class="periyot_adi" @click="setPeriyotColor(4)">4. Periyot</div>
            <div class="periyot_adi" @click="setPeriyotColor(5)">5. Periyot</div>
            <div class="periyot_adi" @click="setPeriyotColor(6)">6. Periyot</div>
            <div class="periyot_adi" @click="setPeriyotColor(7)">7. Periyot</div>
            <div class="periyot_adi gizle">8</div>
            <div class="periyot_adi gizle">9</div>
            <div class="periyot_adi gizle">10</div>
        </div>

        <!-- periyodik tablonun olduğu kısım -->
        <div class="right">
            <div class="tableContent">
              <div class="tables">

              <div class="table">
                <div class="dashboard">
                  dashboard
                </div>
              </div>

              <div class="table" v-for="(e, key) in elementler" :key="key" :class="!e.kutleNumarasi && 'gizle' || getColor(e)">
                <h6 v-if="e.kutleNumarasi">{{e.kutleNumarasi}}</h6>
                <h1 v-if="e.sembol">{{e.sembol}}</h1>
                <h5 v-if="e.adi">{{e.adi}}</h5>
              </div>

            </div>

            </div>
        </div>

      </div>


  </div>
</template>

<script>
import elementler from "./Elementler"

export default {
  name: 'Tablo',
  data(){
    return {
      elementler: elementler,
      colorSet:[
        {
          renk: "mavi",
          elemetler: [1,2,6,7,8,9,10,15,16,17,18,34,35,36,53,54,86,118]
        },
        {
          renk: "sari",
          elemetler: [5,14,32,33,51,52,84,85,116,117]
        },
        {
          renk: "gri",
          elemetler: [57,58,59,60,61,62,63,64,65,66,67,68,69,70,71]
        },
        {
          renk: "kirmizi",
          elemetler: [89,90,91,92,93,94,95,96,97,98,99,100,101,102,103]
        }
      ]
    }
  },
  props: {
    msg: String
  },
  methods: {
    getElement(index){
      return this.elementler.filter(i => i.index == index)[0];
    },
    getColor(e){
      for (const c in this.colorSet) {
        if(this.colorSet[c].elemetler.includes(e.kutleNumarasi)){
            return this.colorSet[c].renk;
        }
      }
      return "blue";
    },
    setPeriyotColor(periyot){

      let periyotColor = [
          {
            periyot: 1,
            elemetler: this.getNumberArr(1,2)
          },
          {
            periyot: 2,
            elemetler: this.getNumberArr(3,10)
          },
          {
            periyot: 3,
            elemetler: this.getNumberArr(11,18)
          },
          {
            periyot: 4,
            elemetler: this.getNumberArr(19,36)
          },
          {
            periyot: 5,
            elemetler: this.getNumberArr(37,54)
          },
          {
            periyot: 6,
            elemetler: this.getNumberArr(55,86)
          },
          {
            periyot: 7,
            elemetler: this.getNumberArr(87,118)
          }
      ]

      let newColorSet = {
          renk: "kirmizi",
          elemetler: periyotColor.filter(i => i.periyot == periyot)[0].elemetler
      }
    
      this.colorSet = [newColorSet];
    
    },getNumberArr(start, finish){
      let arr = [];
      for (let index = start; index < finish + 1; index++) {
        arr.push(index);
      }

      return arr;
    },
    setGrupColor(grup){

      let periyotColor = [
          {
            grup: '1A',
            elemetler: [1,3,11,19,37,55,87]
          },
          {
            grup: '2A',
            elemetler: [4,12,20,38,56,88]
          },
          {
            grup: '3B',
            elemetler: [21,39,57,89]
          },
          {
            grup: '4B',
            elemetler: [22,40,72,104]
          },
          {
            grup: '5B',
            elemetler: [23,41,73,105]
          },
          {
            grup: '6B',
            elemetler: [24,42,74,106]
          },
          {
            grup: '7B',
            elemetler: [25,43,75,107]
          },
          {
            grup: '8B',
            elemetler: [26,44,76,108,27,45,77,109,28,46,78,110]
          },
          {
            grup: '1B',
            elemetler: [29,47,79,111]
          },
          {
            grup: '2B',
            elemetler: [30,48,80,112]
          },
          {
            grup: '3A',
            elemetler: [5,13,31,49,81,113]
          },
          {
            grup: '4A',
            elemetler: [6,14,32,50,82,114]
          },
          {
            grup: '5A',
            elemetler: [7,15,33,51,83,115]
          },
          {
            grup: '6A',
            elemetler: [8,16,34,52,84,116]
          },
          {
            grup: '7A',
            elemetler: [9,17,35,53,85,117]
          },
          {
            grup: '8A',
            elemetler: [2,10,18,36,54,86,118]
          }
      ]


      let newColorSet = {
          renk: "kirmizi",
          elemetler: periyotColor.filter(i => i.grup == grup)[0].elemetler
      }
    
      this.colorSet = [newColorSet];
    }
  }
}
</script>


<style scoped>
.container{
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.footer{
  flex: 1;
  height: 100%;
  width: 100%;
}


.footer .menu{background: #fff;}
.footer .menu .menu-ust{background: #fff;}

.footer .menu .menu-alt{
  display: grid;
  grid-template: 1fr / 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  margin-left: 2.7vw;
  text-align: center;
}

.footer .menu .menu-alt div{
  margin: 0 0.1vw;
  background-color: #ccc;
  padding: 0.2vw;
  cursor: pointer;
}


.center{
  flex: 20;
  position: relative;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: row;
}

.center .left{
  flex: 1;
  display: grid;
  grid-template: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr/ 1fr;
  flex-direction: column;
  margin-right: 0.2vw;
}


.center .left .periyot_adi{
  background-color: #34656d;
  margin: 0.1vw;
  writing-mode:vertical-rl;
  text-align: center;
  color: #fff;
  font-size: 0.8vw;
  padding-right: 0.4vw;
  cursor: pointer;
}

.center .right{
  height: 100%;
  width: 100%;
  flex: 51;
}


.tableContent{
  position: relative;
  height: 100%;
  width: 100%;
}

.tables{
  display: grid;
  height: 100%;
  width: 100%;
  grid-template: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr/ 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
}


.table{
    position: relative;
    opacity: 0.9;
    border: solid 1px #ccc; 
    background: #f1f1f1; 
    margin: 0.1vw;
    font-size:  1.4vw;
    background: #C9D8B6;
    color: #082032;
}

/* sembol */
.table h1{
  margin-top: 0.2vw;
  text-align: center;
  font-size: 2.2vw;
}

/* adı */
.table h5{
  position: absolute;
  width: 100%;
  bottom: 0;
  text-align: center;
  font-size: 0.75vw;
}

/* kutleNumarasi */
.table h6{
  position: absolute;
  top: 0;
  left: 0.2vw;
  font-size: 0.8vw;
}

.table:nth-child(1) {
    opacity: 1;
    background: none;
    border: none;
    grid-row: 1 / 4;
    grid-column: 3 / 13;
    display: flex;
    align-items: flex-end;
    position: relative;
    width: 100%;
    height: 100%;

}


.table:nth-child(4) {
    opacity: 1;
    background: none;
    border: none;
    grid-column: 13 / 18;
    display: flex;
}


.table:nth-child(94) {
    opacity: 1;
    background: none;
    border: none;
    grid-column: 1 / 19;
    display: flex;
}

.table:nth-child(95) {
    opacity: 1;
    background: none;
    border: none;
    grid-column: 1 / 3;
    grid-row: 9 / 11;
    display: flex;
}


.gizle {
    opacity: 0;
    background: none;
    border: none;
}


.gri{
    background: #D1D9D9;
    color: #082032;
}

.yasil{
    background: #C9D8B6;
    color: #082032;
}

.kirmizi{
    background: #FF6767;
    color: #082032;
}

.mavi{
    background: #90a4ae;
    color: #082032;
}

.sari{
    background: #f7b633;
    color: #082032;
}



.dashboard{
  font-size: 1.2vw;
  border-radius: 0.4vw;
  padding: 1vw;
  margin: 1vw;
  position: relative;
  background: #F2E1C1;
  border: solid 1px #003638;
  width: 100%;
}

</style>
