<template>
  <div>
    <button @click="reloadPage()" class="btn btn-dark">NewGame</button>{{space}}
    <button @click="random()" v-bind:disabled = "end"  class="btn btn-dark" >Attack</button>{{space}}
    <button @click="SPrandom()" v-bind:disabled = "end" class="btn btn-dark" >SPAttack</button><br><br> 
    <div class = "col-6" >
        Player : {{selectedplayer.name}}
         {{php}}
      </div>
    <div class="row">
        <div class="col-5">
          <img style="width:25%" :src="selectedplayer.img"  alt="">
        </div>
        <div class="col-2">
          <div class="row">
            <br>
          </div>
          <div class="row">
            <img style="width:10%" :src="versus"  alt="">
          </div>
        </div>
        <br>
        <div class="col-5">
          <img style="width:30%" :src="selectedmonster"  alt="">
    </div>
    </div>
    <br>
    <br>
    <div class = "row">
      <div class = "col-6">
        Monster :{{selectedmonster.name}}
        {{mhp}}
      </div>
    </div>
    <br/>
    <br/>
    <div id="result">
      <div v-if="mhp <= 0">       
        Player win
    </div>
    <div v-else-if="php <= 0">
        Monster win
    </div>
    </div>
    
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      end : false,
      space : "",
      versus : 'https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/a3f544f1-f07b-4aa9-b6f9-824148c31a10/daqrpoq-f7ee01ed-ac8e-4c47-86c9-360f670365d2.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3sicGF0aCI6IlwvZlwvYTNmNTQ0ZjEtZjA3Yi00YWE5LWI2ZjktODI0MTQ4YzMxYTEwXC9kYXFycG9xLWY3ZWUwMWVkLWFjOGUtNGM0Ny04NmM5LTM2MGY2NzAzNjVkMi5wbmcifV1dLCJhdWQiOlsidXJuOnNlcnZpY2U6ZmlsZS5kb3dubG9hZCJdfQ.37GhMgHrxdiLQPB8OPtK_04vGDSUum7EM4vxWzmkzYY',
        monster : [
            'https://i.pinimg.com/originals/9e/b9/94/9eb9947fcd2b0d801f46a4423886eb7b.png',
            'https://i.pinimg.com/originals/2b/f3/0c/2bf30c580585966f90e6d47dc5b6bcdb.png',
            'https://www.models-resource.com/resources/big_icons/5/4115.png',
        ],
        player : [
          {name : "",img :'https://cdn.shopify.com/s/files/1/0701/0143/products/XXRAYPLUS_Zoro__Anime__Turnarounds_01_1024x1024.png?v=1587353230'},
            {name : "",img : 'https://www.sjskgamer.net/wp-content/uploads/2019/09/Kirito-My-Hero.png'},
            {name : "",img : 'https://vignette.wikia.nocookie.net/vsbattles/images/a/a1/Asuna_ALO_copy.png/revision/latest/scale-to-width-down/340?cb=20170507044323'},
        ],
        selectedmonster: {name:"",img:null},
        selectedplayer : {name:"",img:null},
      ppower: "",
      mpoxer: "",
      php: 150,
      mhp: 150,
      term: false,
    };
  },
  methods: {
    reloadPage : function(){
    window.location.reload()
  },
    random: function () {
      this.ppower = Math.floor(Math.random() * 7 + 3);
      this.mhp = this.mhp - this.ppower;
      this.mpower = Math.floor(Math.random() * 7 + 3);
      this.php = this.php - this.mpower;
      if(this.php<=0){
        this.php = 0
        this.end = true
      }else if(this.mhp<=0){
        this.mhp = 0
        this.end = true
      }
    },
    SPrandom: function () {
      this.ppower = Math.floor(Math.random() * 10 + 5);
      this.mhp = this.mhp - this.ppower;
      this.mpower = Math.floor(Math.random() * 10 + 5);
      this.php = this.php - this.mpower;
      if(this.php<=0){
        this.php = 0
        this.end = true
      }else if(this.mhp<=0){
        this.mhp = 0
        this.end = true
      }
    },
    randommonster (items) {
      return items[Math.floor(Math.random()*items.length)];
    },
    randomplayer (items) {
      return items[Math.floor(Math.random()*items.length)];
    },
  },
  created() {
    this.selectedmonster = this.randommonster(this.monster)
    this.selectedplayer = this.randomplayer(this.player)
  },
  
};
</script>

<style>
body{
  background-image: url(https://i.imgur.com/NYFd64r.gif);
  background-position: center;
  background-size: 200%;
}
#result{
  height : 50px;
  font-size : 300%;
  color :yellowgreen;
}
</style>