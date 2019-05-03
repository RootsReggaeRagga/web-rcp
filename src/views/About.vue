<template>
    <div class="about">
        <h1>{{requestAPI}}</h1>
    </div>
</template>

<script>
    // @ is an alias to /src
    import axios from 'axios';
    import Timer from '@/components/Timer.vue';
    import Camera from '@/components/Camera.vue';
    import BootstrapVue from 'bootstrap-vue';
    import 'bootstrap/dist/css/bootstrap.css';
    import 'bootstrap-vue/dist/bootstrap-vue.css';

    export default {
        name: 'RequestAPI',
        methods: {
            requestAPI() {
                axios.post('https://admin.workguard.app/api/v1/devices?', {
                    body: {
                        'email': 'bartlomiej.grela@gmail.com',
                        'password': 'bartek72',
                        'serial': '123456789',
                        'api-key': '1234qwer',
                        'device-name': 'bartek device'
                    }
                })
                    .then(function (response) {
                        console.log(response);
                    })
                    .catch(function (error) {
                        console.log(error);
                    })
                    .then(function () {
                        // always executed
                    });
            }
        },
        mounted() {
            this.requestAPI = this.requestAPI();
        }

    }
</script>