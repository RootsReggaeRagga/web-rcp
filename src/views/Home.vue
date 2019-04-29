<template>
    <div class="home">
        <div class="container">
            <div class="row">
                <div class="col-md-6">
                    <Camera/>
                    <!--<HelloWorld msg="Welcome to Your Vue.js App"/>-->
                </div>
                <div class="col-md-6">
                    <Timer/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    // @ is an alias to /src
    import HelloWorld from '@/components/HelloWorld.vue';
    import Timer from '@/components/Timer.vue';
    import Camera from '@/components/camera.vue';
    import BootstrapVue from 'bootstrap-vue';
    import 'bootstrap/dist/css/bootstrap.css';
    import 'bootstrap-vue/dist/bootstrap-vue.css';

    export default {
        name: 'home',
        components: {
            HelloWorld, Timer, Camera
        }
    }
</script>
<style scoped lang="scss">
    .home{
        background: #1c2c50;
        height:100vh;
        display:flex;
        align-items: center;
        justify-content: center;
        align-content: center;
    }
</style>