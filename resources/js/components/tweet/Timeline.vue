<template>
    <div class="card">
        <div class="card-header">Timeline</div>

        <div class="card-body">
            <post :tweets="tweets"></post>

            <hr>

            <div class="media mb-3" v-for="(tweet, index) in tweets" :key="index">
                <img class="mr-3" style="width:30px" src="img/tweet.png" alt="Generic placeholder image">
                <div class="media-body">
                    <h5 class="mt-0">{{ tweet.user.name }}</h5>
                    {{ tweet.body }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Post from "./Post";

export default {
    data () {
        return {
            tweets: []
        }
    },
    components: {
        Post
    },
    mounted () {
        axios.get('/tweets').then((response) => {
            this.tweets = response.data;
        }).catch((err) => {
            console.log(err)
        });
    }
}
</script>
