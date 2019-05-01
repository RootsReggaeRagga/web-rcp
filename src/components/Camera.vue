<template>
    <div id="Camera">
        <div>
            <video ref="video" id="video" :width="width"
                   :height="height"
                   :autoplay="autoplay"
                   :playsinline="playsinline"></video>
        </div>
        <div>
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
                default: true
            },
            screenshotFormat: {
                type: String,
                default: "image/jpeg"
            },
            deviceId: {
                type: String,
                default: null
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
                    this.video.src = stream;
                    //this.video.play();
                });
            }
        },
        methods: {
            capture() {
                this.canvas = this.$refs.canvas;
                var context = this.canvas.getContext("2d").drawImage(this.video, 0, 0, this.width, this.height);
                this.captures.push(canvas.toDataURL("image/png"));
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

    li {
        display: inline;
        padding: 5px;
    }
</style>