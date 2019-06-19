<template>
<div class="body">
    <section class="player">
        <div class="cover">
            <img :src="coverUrl" alt="album cover">
        </div>
        <div class="control">
            <audio :src="'https://sunly.in/music/njlizhi/studio_album/' + albumName + '/' + srcName" controls preload="none"></audio>
        </div>
    </section>
    <section>
        <ul>
            <li v-for="(item, index) in songsArr"
                :key="index"
                @click="handleClickSongsName(item)">
                {{item.name}}
            </li>
        </ul>
    </section>
</div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Player',
    data () {
        return {
            songsArr: [],
            coverUrl: '',
            srcName: ''
        }
    },
    props: {
        albumName: String
    },
    mounted() {
        this.getSongs()
    },
    watch: {
        albumName () {
            this.coverUrl = 'https://sunly.in/music/njlizhi/studio_album/' + this.albumName + '/cover.jpg'
            this.getSongs()
        }
    },
    methods: {
        getSongs () {
            if (this.albumName) {
                axios.get('https://api.github.com/repos/sjx1995/njlizhi/contents/studio_album/' + this.albumName).then(this.getSongsSuc)
            }
        },
        getSongsSuc (res) {
            let songsArr = []
            if (res && res.status === 200) {
                let data = res.data
                for (let i = 0; i < data.length; i ++) {
                    if (data[i].name.indexOf('.ogg') > -1) {
                        let songDetail = {}
                        songDetail.name = data[i].name
                        songDetail.downloadUrl = data[i].download_url
                        songsArr.push(songDetail)
                    }
                }
            }
            this.songsArr = songsArr
        },
        handleClickSongsName (item) {
            this.srcName = item.name
        }
    }
}
</script>

<style lang="stylus" type="text/stylus" scoped>
div.body
    margin 80px auto
    section.player
        div.cover,
        div.control
            text-align center
            padding-bottom 20px
            img
                width 250px
                height 100%
    section
        ul
            li
                cursor pointer
                font-size 18px
                line-height 30px
                text-align center
</style>