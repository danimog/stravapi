<template>
    <div>
        <v-container class="text-center">
            <h1>STRAVA-API</h1>
            <!-- {{dati}} -->
            <ul>
                <li v-for="res in dati.segments" :key="res.id">

                    <b>ID:</b> {{res.id}} | <b>nome:</b> {{res.name}} | <b>Distanza:</b> {{res.distance}}m | 
                    <b>dislivello:</b> {{res.elev_difference}}+ | <b>cat. salita:</b> {{res.climb_category}} | <b>pendenza media:</b> {{res.avg_grade}}%
                </li>
            </ul>
        </v-container>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name: 'MyHome',
        data: () => ({
            bounds: ['44.0737', '9.5983', '44.1514', '9.81'],
            activity: 'running',
            dati: null,
            error: null,
        }),
        created: function(){
            this.getMyAPI();
        },
        methods:{
            // getStravaAPI(){
            //     var StravaApiV3 = require('strava_api_v3');
            //     var defaultClient = StravaApiV3.ApiClient.instance;

            //     // Configure OAuth2 access token for authorization: strava_oauth
            //     var strava_oauth = defaultClient.authentications['strava_oauth'];
            //     strava_oauth.accessToken = 'e76004ffbc2e445b3f5b4108830d16645d1e99d6'

            //     var api = new StravaApiV3.SegmentsApi()

                
            //     var opts = { 
            //         'activityType': activityType_example, // {String} Desired activity type.
            //         'minCat': 56, // {Integer} The minimum climbing category.
            //         'maxCat': 56 // {Integer} The maximum climbing category.
            //     };

            //     var callback = function(error, data, response) {
            //         if (error) {
            //             console.error(error);
            //         } else {
            //             console.log('API called successfully. Returned data: ' + data);
            //         }
            //     };
            //     api.exploreSegments(this.bounds, opts, callback);
            // }

            async getMyAPI(){
                let url = 'https://www.strava.com/api/v3/segments/explore?access_token=8d2d733148ea309468d4f8ebcde8dc6557db869e&bounds=44.1324,9.6692,44.155,9.7143';
                
                // 44.0737,9.5983,44.1514,9.81
                try {
                    this.dati = await axios.get(url).then(res => res.data);
                    this.error = null;
                    console.log(this.dati);
                } catch (error) {
                    this.dati = null;
                    this.error = error;
                    console.log("errore! "+error)
                }

            }
        }
        

    }
</script>

<style lang="scss" scoped>

</style>