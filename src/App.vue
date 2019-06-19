<template>
    <div id="app">
        <header-temp @clickAbout="showAboutFun" @clickAlbum="showAlbumFun" @firstAlbum="showFirstAlbum"></header-temp>
        <player v-show="!showAbout" :albumName="this.albumName"></player>
        <about v-show="showAbout" @hiddenAbout="hiddenAbout"></about>
        <footer-temp></footer-temp>
    </div>
</template>

<script>
    import HeaderTemp from './components/Header'
    import Player from './components/Player'
    import FooterTemp from './components/Footer'
    import About from './components/About'

    export default {
        name: 'app',
        data() {
            return {
                showAbout: false,
                albumName: ''
            }
        },
        components: {
            HeaderTemp,
            Player,
            FooterTemp,
            About
        },
        methods: {
            showAboutFun () {
                this.showAbout = true
            },
            showAlbumFun (data) {
                this.showAbout = false
                this.albumName = data.albumName
            },
            showFirstAlbum (data) {
                this.albumName = data
            },
            hiddenAbout () {
                this.showAbout = false
            }
        }
    }
</script>

<style lang="stylus" type="text/stylus" scoped>

</style>
