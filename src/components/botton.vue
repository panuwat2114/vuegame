<template>
  <div>
    <div class="row">
      <div class="col-sm">
        <p style="font-size: 150%">{{aplayer.name}}</p>
        <p>
          <img v-bind:style="{width: aplayer.hp + 'px'}" :src="hp1" alt height="20px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{aplayer.hp}}</p>
        <p>
          <img style="width:70%" :src="aplayer.image" />
        </p>
      </div>
      <div class="col-sm">
        <div class="row">
          <div class="col">
            <button v-bind:disabled="end" class="btn btn-primary" @click="start()">Start</button>
          </div>
          <div class="col">
            <button v-bind:disabled="end" class="btn btn-danger" @click="attack()">Attack</button>
          </div>
          <div class="col-4">
            <button v-bind:disabled="end" class="btn btn-success" @click="special()">SpecialAttack</button>
          </div>
          <div class="col">
            <button class="btn btn-warning" @click="reset()">NewGame</button>
          </div>
          <br />
          <img
            src="https://www.pnglib.com/wp-content/uploads/2020/01/versus-battle_5e17065fdd515.png"
            width="90%"
          />
        </div>
        <div class="row">
          <div class="col-sm"></div>
          <div class="col-sm">
            <div id="score">
              <div v-if="amonster.hp <= 0">Player Win</div>
              <div v-else-if="aplayer.hp <= 0">Monster Win</div>
            </div>
          </div>
          <div class="col-sm"></div>
        </div>
      </div>
      <div class="col-sm">
        <p style="font-size: 150%">{{amonster.name}}</p>
        <p>
          <img v-bind:style="{width: amonster.hp + 'px'}" :src="hp2" alt height="15px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{amonster.hp}}</p>
        <p>
          <img style="width:70%" :src="amonster.image" />
        </p>
      </div>
    </div>
    <hr />
    <div class="row">
      <div class="col"></div>
      <div class="col-6">
        <div class="card bg-dark">
          <div class="card-header">วิธีการเล่นเกม</div>
          <div class="card-body">
            <p>1.กดปุ่ม Start เพื่อทําการ Ramdom ตัวละครทั้ง 2 ฝ่าย</p>
            <p>2.กดปุ่ม Attack เพื่อทำ Damage ใส่อีกฝ่ายและถูกโจมตีในเวลาเดียวกันแบบธรรมดา</p>
            <p>3.กดปุ่ม Special Attack เพื่อทำ Damage ใส่อีกฝ่ายและถูกโจมตีในเวลาเดียวกันแบบโจมตีพิเศษ</p>
            <p>4.กดปุ่ม New Game เพื่อทําการเริ่มเล่นเกมใหม่</p>
          </div>
        </div>
      </div>
      <div class="col"></div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      thp: "HP:",
      end: false,
      hp2:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      hp1:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      aplayer: { name: "", hp: 1, image: "", hp1: "" },
      player: [
        {
          name: "Boruto",
          hp: 300,
          image:
            "https://i.pinimg.com/originals/9e/b9/94/9eb9947fcd2b0d801f46a4423886eb7b.png",
        },
        {
          name: "Sasuke",
          hp: 375,
          image:
            "https://i.pinimg.com/originals/2b/f3/0c/2bf30c580585966f90e6d47dc5b6bcdb.png",
        },
        {
          name: "Goku",
          hp: 450,
          image:
            "https://www.models-resource.com/resources/big_icons/5/4115.png",
        },
      ],
      amonster: { name: "", hp: 1, image: "", hp1: "" },
      monster: [
        {
          name: "Zoro",
          hp: 330,
          image:
            "https://cdn.shopify.com/s/files/1/0701/0143/products/XXRAYPLUS_Zoro__Anime__Turnarounds_01_1024x1024.png?v=1587353230",
        },
        {
          name: "Kirito",
          hp: 400,
          image:
            "https://www.sjskgamer.net/wp-content/uploads/2019/09/Kirito-My-Hero.png",
        },
        {
          name: "Arsuna",
          hp: 350,
          image:
            "https://vignette.wikia.nocookie.net/vsbattles/images/a/a1/Asuna_ALO_copy.png/revision/latest/scale-to-width-down/340?cb=20170507044323",
        },
      ],
      pmax: "",
      mmax: "",
    };
  },
  methods: {
    randomno: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      this.aplayer = this.player[this.randomno(1, 3) - 1];
      this.amonster = this.monster[this.randomno(1, 3) - 1];
    },
    attack: function () {
      this.pmax = Math.floor(Math.random() * 10 + 4);
      this.amonster.hp = this.amonster.hp - this.pmax;
      this.mmax = Math.floor(Math.random() * 10 + 4);
      this.aplayer.hp = this.aplayer.hp - this.mmax;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    special: function () {
      this.pmax = Math.floor(Math.random() * 15 + 6);
      this.amonster.hp = this.amonster.hp - this.pmax;
      this.mmax = Math.floor(Math.random() * 15 + 6);
      this.aplayer.hp = this.aplayer.hp - this.mmax;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>
<style>
#score {
  font-size: 300%;
  color: orange;
}
</style>