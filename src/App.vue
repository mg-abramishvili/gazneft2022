<template>
    <div class="wrapper">
        <flipbook class="flipbook" ref="flipbook"
            :pages="pages"
            :zooms=null
            :singlePage=false
            :clickToZoom=false
        ></flipbook>

        <div class="panel-left">
            <button v-if="views.prevButton" @click="prevPage()">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-left-short" viewBox="0 0 16 16">
                    <path fill-rule="evenodd" d="M12 8a.5.5 0 0 1-.5.5H5.707l2.147 2.146a.5.5 0 0 1-.708.708l-3-3a.5.5 0 0 1 0-.708l3-3a.5.5 0 1 1 .708.708L5.707 7.5H11.5a.5.5 0 0 1 .5.5z"/>
                </svg>
            </button>

            <button v-if="views.homeButton" @click="goHome()">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-house" viewBox="0 0 16 16">
                    <path fill-rule="evenodd" d="M2 13.5V7h1v6.5a.5.5 0 0 0 .5.5h9a.5.5 0 0 0 .5-.5V7h1v6.5a1.5 1.5 0 0 1-1.5 1.5h-9A1.5 1.5 0 0 1 2 13.5zm11-11V6l-2-2V2.5a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 .5.5z"/>
                    <path fill-rule="evenodd" d="M7.293 1.5a1 1 0 0 1 1.414 0l6.647 6.646a.5.5 0 0 1-.708.708L8 2.207 1.354 8.854a.5.5 0 1 1-.708-.708L7.293 1.5z"/>
                </svg>
            </button>
        </div>

        <div class="panel-right">
            <button v-if="views.nextButton" @click="nextPage()">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-right-short" viewBox="0 0 16 16">
                    <path fill-rule="evenodd" d="M4 8a.5.5 0 0 1 .5-.5h5.793L8.146 5.354a.5.5 0 1 1 .708-.708l3 3a.5.5 0 0 1 0 .708l-3 3a.5.5 0 0 1-.708-.708L10.293 8.5H4.5A.5.5 0 0 1 4 8z"/>
                </svg>
            </button>
        </div>

        <v-idle :duration="60" :events="['click', 'touchstart', 'touchmove', 'touchend', 'mousemove', 'scroll']" @idle="goHome()" />
    </div>
</template>

<script>
    import Flipbook from 'flipbook-vue'

    export default {
        data() {
            return {
                pages: [ // 2160x3054px per page for horizontal flip book
                    null,
                    '/pages/00.jpg',
                    '/pages/01.jpg',
                    '/pages/02.jpg',
                    '/pages/03.jpg',
                    '/pages/04.jpg',
                    '/pages/05.jpg',
                    '/pages/06.jpg',
                    '/pages/07.jpg',
                    '/pages/08.jpg',
                    '/pages/09.jpg',
                    '/pages/10.jpg',
                    '/pages/11.jpg',
                    '/pages/12.jpg',
                    '/pages/13.jpg',
                    '/pages/14.jpg',
                    '/pages/15.jpg',
                    '/pages/16.jpg',
                    '/pages/17.jpg',
                    '/pages/18.jpg',
                    '/pages/19.jpg',
                    '/pages/20.jpg',
                    '/pages/21.jpg',
                    '/pages/22.jpg',
                    '/pages/23.jpg',
                    '/pages/24.jpg',
                    '/pages/25.jpg',
                    '/pages/26.jpg',
                    '/pages/27.jpg',
                    '/pages/28.jpg',
                    '/pages/29.jpg',
                    '/pages/30.jpg',
                    '/pages/31.jpg',
                    '/pages/32.jpg',
                    '/pages/33.jpg',
                    '/pages/34.jpg',
                    '/pages/35.jpg',
                    '/pages/36.jpg',
                    '/pages/37.jpg',
                    '/pages/38.jpg',
                    '/pages/39.jpg',
                    '/pages/40.jpg',
                    '/pages/41.jpg',
                    '/pages/42.jpg',
                    '/pages/43.jpg',
                    '/pages/44.jpg',
                    '/pages/45.jpg',
                    '/pages/46.jpg',
                    '/pages/47.jpg',
                    '/pages/48.jpg',
                    '/pages/49.jpg',
                    '/pages/50.jpg',
                    '/pages/51.jpg',
                    '/pages/52.jpg',
                    '/pages/53.jpg',
                    '/pages/54.jpg',
                    '/pages/55.jpg',
                    '/pages/56.jpg',
                    '/pages/57.jpg',
                    '/pages/58.jpg',
                    '/pages/59.jpg',
                    '/pages/60.jpg',
                    '/pages/61.jpg',
                    '/pages/62.jpg',
                    '/pages/63.jpg',
                    '/pages/64.jpg',
                    '/pages/65.jpg',
                    '/pages/66.jpg',
                    '/pages/67.jpg',
                    '/pages/68.jpg',
                    '/pages/69.jpg',
                    '/pages/70.jpg',
                    '/pages/71.jpg',
                    '/pages/72.jpg',
                    '/pages/73.jpg',
                    '/pages/74.jpg',
                    '/pages/75.jpg',
                    '/pages/76.jpg',
                    '/pages/77.jpg',
                    '/pages/78.jpg',
                    '/pages/79.jpg',
                    '/pages/80.jpg',
                    '/pages/81.jpg',
                ],

                views: {
                    prevButton: false,
                    nextButton: true,
                    homeButton: false,
                }
            }
        },
        mounted() {
            this.$watch(
                () => {
                    return this.$refs.flipbook.currentPage
                },
                () => {
                    if(this.$refs.flipbook.currentPage == 0) {
                        this.views.prevButton = false
                        this.views.nextButton = true
                        this.views.homeButton = false
                        return
                    }
                    if(this.$refs.flipbook.currentPage == 82) {
                        this.views.prevButton = true
                        this.views.nextButton = false
                        this.views.homeButton = true
                        return
                    }

                    this.views.prevButton = true
                    this.views.nextButton = true
                    this.views.homeButton = true
                }
            )

            document.oncontextmenu = new Function("return false;")
        },
        methods: {
            prevPage() {
                this.$refs.flipbook.flipLeft()
            },
            nextPage() {
                this.$refs.flipbook.flipRight()
            },
            goHome() {
                if(this.$refs.flipbook.currentPage > 0) {
                    this.$refs.flipbook.goToPage(0)
                }
            },
        },
        components: {
            Flipbook
        }
    }
</script>

<style>
    html, body {
        margin: 0;
        position: relative;
        width: 1920px;
        height: 1080px;
        overflow: hidden;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
        -webkit-touch-callout: none;
        -khtml-user-select: none;
        cursor: none;
    }
    .wrapper {
        position: relative;
        width: 100%;
        height: 100%;
        overflow: hidden;
        background-color: #00B0E2;
    }
    .flipbook {
        width: 77.55%;
        height: 98%;
        margin: 0 auto;
        margin-top: 1vh;
    }
    .flipbook .bounding-box {
        box-shadow: 0 0 20px rgba(0,0,0,0.45);
    }
    .panel-left,
    .panel-right {
        width: 6vh;
        position: absolute;
        top: 45%;
        padding: 1vh 0;
    }
    .panel-left {
        left: 7vh;
    }
    .panel-right {
        right: 7vh;
    }
    .panel-left button,
    .panel-right button {
        background-color: #005E9B;
        width: 6vh;
        height: 6vh;
        box-shadow: none;
        border: 0;
        border-radius: 1vh;
        margin: 1vh 0;
    }
    .panel-left button svg,
    .panel-right button svg {
        width: 100%;
        height: 100%;
        color: #fff;
    }
    .panel-left button:nth-of-type(2) {
        margin-top: 36vh;
    }
    .panel-left button:nth-of-type(2) svg {
        width: 70%;
        height: 70%;
    }
</style>
