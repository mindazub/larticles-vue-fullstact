<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">

                    <div class="card card-body" v-for="article in articles" v-bind:key="article.id">
                        <div class="card-header">{{ article.title }}</div>

                        <div class="card-body">
                            {{ article.body }}
                        </div>
                    </div>

            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                articles: [],
                article: {
                    id: '',
                    title: '',
                    body: ''
                },
                article_id: '',
                pagination: {},
                edit: false
            }
        },
        created() {
            this.fetchArticles();
        },
        mounted() {
            console.log('articles mounted.')
        },
        methods: {
            fetchArticles() {
                fetch('api/article')
                    .then(res => res.json())
                    .then(res => {
                        console.log(res.data);
                    })
            }
        }
    }
</script>
