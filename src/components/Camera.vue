<template>
    <div id="Camera">
        <div>
            <video ref="video" id="video" :width="width"
                   :height="height"
                   :poster="poster"
                   :autoplay="autoplay"
                   :playsinline="playsinline"></video>
        </div>
        <div>
            <button class="btn btn-primary btn-rounded" id="start" v-on:click="startCamera()">Rozpocznij</button>
            <button class="btn btn-danger btn-rounded" id="snap" v-on:click="capture()">Selfiaczek pyk!</button>
        </div>
        <canvas ref="canvas" id="canvas" width="640" height="480"></canvas>
        <ul>
            <li v-for="c in captures">
                <img v-bind:src="c" height="50"/>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'Camera',
        props: {
            width: {
                type: [Number, String],
                default: "100%"
            },
            height: {
                type: [Number, String],
                default: 500
            },
            autoplay: {
                type: Boolean,
                default: false
            },
            screenshotFormat: {
                type: String,
                default: "image/webp"
            },
            poster:{
                type: String,
                default: "poster.png"
            },
            playsinline: {
                type: Boolean,
                default: true
            },
            resolution: {
                type: Object,
                default: null,
                validator: value => {
                    return value.height && value.width;
                }
            }
        },
        data() {
            return {
                video: {},
                canvas: {},
                captures: []
            }
        },
        mounted() {
            this.video = this.$refs.video;
            if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
                navigator.mediaDevices.getUserMedia({video: true}).then(stream => {
                    this.video.srcObject=stream;
                    //this.video.play();
                });
            }
        },
        methods: {
            capture() {
                this.canvas = this.$refs.canvas;
                var context = this.canvas.getContext("2d").drawImage(this.video, 0, 0, 640, 480);
                this.captures.push(canvas.toDataURL("image/webp"));
                this.video.stop();
            },
            startCamera(){
                this.video.play()
            }
        }
    }
</script>
<style>

    #video {
        background-color: #000000;
    }

    #canvas {
        display: none;
    }
    ul{
        height:60px;
    }
    li {
        display: inline;
        padding: 5px;
        margin-bottom:10px;
    }
</style>