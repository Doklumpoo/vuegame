<template>
<div>
    <div class="row">
        <div class="col-6">
            <h1>Player</h1>
            {{aPlayer.name}}
            <br />
            <img :src="hp1" height="40px" />
            HP {{aPlayer.hp}}
        </div>
        <div class="col-6">
            <h1>Monster</h1>
            {{aMonster.name}}
            <br />
            <img :src="hp2" height="40px" />
            HP {{aMonster.hp}}
        </div>
    </div>
    <div class="row">
        <div class="col-5">
            <br />
            <div style="position: absolute; z-index: 1;"><img style="width:750px" :src="aura"></div>
            <div style="position: absolute; z-index: 2;"><img style="width:50%" :src="aPlayer.img" /></div>
        </div>

        <div class="col-sm">
            <br />
            <div v-if="aMonster.hp <=0 ">You Win <br><br />
                <img src="https://papuarza.github.io/project-game-pacman/img/monster-red.gif" width="60%">
            </div>
            <div v-else-if="aPlayer.hp <= 0 ">You Lose <br><br />
                <img src="https://papuarza.github.io/project-game-pacman/img/monster-yellow.gif" width="60%">
            </div>
            <br />
            <br />
            <br />
            <img src="https://www.pngmart.com/files/11/Versus-PNG-Clipart.png" width="50%" />
        </div>
        <div class="col-5">
            <br />
            <div style="position: absolute; z-index: 3;"><img style="width:750px" :src="aura"></div>
            <div style="position: absolute; z-index: 4;"><img style="width:50%" :src="aMonster.img" /></div>
        </div>
    </div>
    <br />
    <br />
    <br />
    <br />
    <div class="d-flex justify-content-center">
        <div class="but">
            <div class="col">
                <button @click="start()" class="btn btn-light ml-2">Start</button>
                <button v-bind:disabled="end" @click="attack()" class="btn btn-light ml-2">Attack</button>
                <button v-bind:disabled="end" @click="specialattack()" class="btn btn-light ml-2">Special Attack</button>
                <button @click="reset()" class="btn btn-light ml-2">Reset</button>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            aura: "https://i.pinimg.com/originals/cd/14/68/cd1468741cb6d85d2b9d84b9ca6d1829.gif",
            win: "https://thumbs.gfycat.com/ContentNecessaryHorseshoebat-max-1mb.gif",
            playmax: "",
            monsmax: "",
            hp1: "https://thumbs.gfycat.com/MixedBiodegradableBluetonguelizard-size_restricted.gif",
            hp2: "https://thumbs.gfycat.com/MixedBiodegradableBluetonguelizard-size_restricted.gif",
            end: false,
            aPlayer: {
                name: "",
                hp: "",
                img: "",
                hp1: ""
            },
            player: [{
                    name: "Doraemon",
                    hp: 150,
                    image: "https://stickershop.line-scdn.net/stickershop/v1/product/1671/LINEStorePC/main.png;compress=true"
                },
                {
                    name: "Doraemee",
                    hp: 200,
                    image: "https://stickershop.line-scdn.net/stickershop/v1/product/936/LINEStorePC/main.png;compress=true"
                },
                {
                    name: "Shisuga",
                    hp: 250,
                    image: "https://doraemonfc.files.wordpress.com/2014/02/chara_image3.png"
                },
                {
                    name: "Suneo",
                    hp: 300,
                    image: "https://doraemonfc.files.wordpress.com/2014/02/chara_image5.png"
                },
            ],
            aMonster: {
                name: "",
                hp: "",
                img: "",
                hp2: ""
            },
            monster: [{
                    name: "Dekashi",
                    hp: 150,
                    image: "https://4.bp.blogspot.com/-5noChB0yGoc/WgE36NXO0eI/AAAAAAABMnc/C-4Iq5fAayEF9Q9MwPW4aUe97ul43jlcQCKgBGAs/s1600/footer_chara%2B%25281%2529.png"
                },
                {
                    name: "Luna",
                    hp: 200,
                    image: "https://vignette.wikia.nocookie.net/th-doraemon/images/f/fb/Chara_luna_%281%29_%282%29.png/revision/latest/scale-to-width-down/340?cb=20181226105638"
                },
                {
                    name: "Nobita",
                    hp: 250,
                    image: "https://sites.google.com/site/pangweb12/_/rsrc/1487331408404/-nobita/No-bita.png"
                },
                {
                    name: "GiAnt",
                    hp: 300,
                    image: "https://sites.google.com/site/eadpattaraporn029/_/rsrc/1455434440194/home/do-ra-xe-mxn/prawati-ci-xae-nth/chara_image4.png?height=320&width=228"
                },
            ],
        };
    },
    methods: {
        randomDamage: function (min, max) {
            return Math.max(Math.floor(Math.random() * max) + 1, min);
        },
        start: function () {
            //1.random 1-3--> ชื่อ hp รูป
            this.aPlayer = this.player[this.random(1, 4) - 1];
            this.aMonster = this.monster[this.random(1, 4) - 1];
        },
        attack: function () {
            this.playmax = Math.floor(Math.random() * 10 + 5);
            this.aPlayer.hp = this.aPlayer.hp - this.playmax;
            this.monsmax = Math.floor(Math.random() * 10 + 5);
            this.aMonster.hp = this.aMonster.hp - this.monsmax;
            if (this.aPlayer.hp <= 0) {
                this.aPlayer.hp <= 0;
                this.end = true;
            } else if (this.aMonster.hp <= 0) {
                this.aMonster.hp <= 0;
                this.end = true;
            }

            //player-->monstor
            //player<--monster
            //player.HP<=0 ==> ?
            //monster.HP<==0 ==> ?
            //End Game

        },
        specialattack: function () {
            this.playmax = Math.floor(Math.random() * 15 + 5);
            this.aPlayer.hp = this.aPlayer.hp - this.playmax;
            this.monsmax = Math.floor(Math.random() * 15 + 5);
            this.aMonster.hp = this.aMonster.hp - this.monsmax;
            if (this.aPlayer.hp <= 0) {
                this.aPlayer.hp = 0;
                this.end = true;
            } else if (this.aMonster.hp <= 0) {
                this.aMonster.hp = 0;
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
div {
    font-size: 35px;
    color: rgb(13, 14, 13);
    margin: 0;
    padding: 0;
}

.but {
    position: fixed;
    bottom: 50px;
}
</style>
