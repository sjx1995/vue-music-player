<template>
    <header>
        <ul>
            <li>@南京李志</li>
            <li v-for="(item, index) in albumList" :key="index" @click="handleClickAlbum(item)">{{item}}</li>
            <li @click="handleClickAbout">关于</li>
        </ul>
    </header>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Header',
    data () {
        return {
            albumList: []
        }
    },
    methods: {
        handleClickAbout () {
            this.$emit('clickAbout')
        },
        handleClickAlbum (albumName) {
            let data = {
                albumName: albumName
            }
            this.$emit('clickAlbum', data)
        },
        getAlbum () {
            axios.get('https://api.github.com/repos/sjx1995/njlizhi/contents/studio_album').then(this.getAlbumSuc)
            // axios.get('https://sunly.in/music/njlizhi/studio_album.json').then(this.getAlbumSuc)
        },
        getAlbumSuc (res) {
            if (res && res.status === 200) {
                let data = res.data
                let albumList = []
                for (let i = 0; i < data.length; i++) {
                    albumList.push(data[i].name)
                }
                this.$emit('firstAlbum', albumList[0])
                this.albumList = albumList
            }
        }
    },
    mounted() {
        this.getAlbum()
    }
}
</script>

<style lang="stylus" type="text/stylus" scoped>
header
    height 48px
    z-index 999
    background #333333
    color: #ffffff
    line-height 48px
    position fixed
    top 0
    left 0
    right 0
    ul
        li
            float left
            display inline-block
            padding 0 10px
            cursor pointer
            &:hover
                background-color #5e5e5e
            &:first-child
                background-color #333333
                cursor default
            &:last-child
                float right
</style>