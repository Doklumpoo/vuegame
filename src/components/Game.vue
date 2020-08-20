<template>
  <div>
    <p>
      HP Player {{randomDamage(1,3)}}
      {{ player[randomDamage(1,3)-1].name}}
    </p>

    <hr />
    name= {{aplayer.name}}
    hp= {{aplayer.hp}}
    image= {{aplayer.image}}
    <hr />
    <p>
      HP Monter {{randomDamage(1,3)}}
      {{ monster[randomDamage(1,3)-1].name}}
    </p>
    <button @click="start()">Start</button>
    <button @click="attack()">Attack</button>
  </div>
</template>
<script>
export default {
  data: function () {
    return {
      aplayer: {
        name: "",
        hp: 0,
        image: "",
      },

      player: [
        { name: "Doraemon", hp: 150, image: "https://b1.pngbarn.com/png/296/822/doraemon-1-doraemon-png-clip-art-thumbnail.png"},
        { name: "Anakin", hp: 200, image: "https://b1.pngbarn.com/png/478/508/star-wars-revenge-of-the-sith-anakin-skywalker-png-clip-art.png" },
        { name: "Skywalke", hp: 250, image: "https://e7.pngegg.com/pngimages/932/839/png-clipart-anakin-skywalker-open-graphics-white-auto-racing-poster-design-fictional-character-anakin-skywalker.png" },
        { name: "Iron man", hp: 300, image: "https://toppng.com/uploads/preview/ew-iron-man-high-quality-wallpapers-imagenes-de-iron-ma-11562854157bma8fh56nn.png" },
      ],
      monster: [
        { name: "Thanos", hp: 150, image: "https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/5b8d2b12-21e8-4931-8a6d-fb9ecdd60383/dc5ro2y-020a589a-a529-46d2-a973-bb811389e8c0.png/v1/fill/w_515,h_1280,strp/avengers_infinity_war_thanos_png_by_metropolis_hero1125_dc5ro2y-fullview.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3siaGVpZ2h0IjoiPD0xMjgwIiwicGF0aCI6IlwvZlwvNWI4ZDJiMTItMjFlOC00OTMxLThhNmQtZmI5ZWNkZDYwMzgzXC9kYzVybzJ5LTAyMGE1ODlhLWE1MjktNDZkMi1hOTczLWJiODExMzg5ZThjMC5wbmciLCJ3aWR0aCI6Ijw9NTE1In1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmltYWdlLm9wZXJhdGlvbnMiXX0.EfDeMFz_MEJg6l29GXKNwjJq35bRufCsspZKDFeSGeQ" },
        { name: "Darth vader", hp: 200, image: "https://pngimg.com/uploads/darth_vader/darth_vader_PNG14.png" },
        { name: "Nobita", hp: 250, image: "https://sites.google.com/site/pangweb12/_/rsrc/1487331408404/-nobita/No-bita.png" },
        { name: "GiAnt", hp: 300, image: "https://i7.pngguru.com/preview/181/102/515/shizuka-minamoto-doraemon-nobita-nobi-version-vector.jpg" },
      ],
    };
  },
  methods: {
    randomDamage: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      //1.random 1-3--> ชื่อ hp รูป
      this.aplayer = this.player[this.randomNo(1, 3) - 1];
    },
    attack: function () {
      //player-->monstor
      //player<--monster
      //player.HP<=0 ==> ?
      //monster.HP<==0 ==> ?
      //End Game
    },
  },
};
</script>