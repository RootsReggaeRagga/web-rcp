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
                const formData = new FormData();
                formData.append('email', 'bartlomiej.grela@agencja71.pl');
                formData.append('password', 'bartek72');
                formData.append('serial', 'bartlomiej.grela@agencja71.pl');
                formData.append('device-name', 'bartlomiej.grela@agencja71.pl');
                formData.append('api-key', 'bartlomiej.grela@agencja71.pl');
                //formData.append('_password', password);

                axios
                    .post('https://test.workguard.app/api/v1/devices', formData)
                    .then(response => {
                        console.log(response.data);
                    })
               /* axios.get('https://test.workguard.app/api/v1/test', {
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    params: {
                        'value': '1234'

                    }
                })
                    .then(function (response) {
                        console.log(response.data);
                    })
                    .catch(function (error) {
                        console.log(error);
                    })
                    .then(function () {
                        // always executed
                    });*/
            }
        },
        mounted() {
            this.requestAPI = this.requestAPI();
        }

    }
</script>