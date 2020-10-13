<template>
    <div class="columns">
        <div class="column is-one-quarter no-padding">
            <SubscriptionList @change-active-subscription="setActiveSubscription"></SubscriptionList>
        </div>
        <div class="column no-padding">
            <ArticleList :feedUrl="feedUrl"/>
        </div>
    </div>
</template>

<script>
    import SubscriptionList from './components/SubscriptionList'
    import ArticleList from "./components/ArticleList";

    export default {
        name: 'App',
        components: {
            ArticleList,
            SubscriptionList
        },
        data() {
            return {
                feedUrl: ''
            };
        },
        methods: {
            setActiveSubscription(url) {
                this.feedUrl = url;
            },
        },
    }
</script>

<style lang="scss">
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: left;
        padding: 8px;
        color: #2c3e50;
    }

    .column.no-padding {
        padding: 0;
    }

    .ellipsis {
        text-overflow: ellipsis;
        white-space: nowrap;
        overflow: hidden;
    }

    .loader {
        margin: 100px auto;
        font-size: 25px;
        width: 1em;
        height: 1em;
        border-radius: 50%;
        position: relative;
        text-indent: -9999em;
        -webkit-animation: load5 1.1s infinite ease;
        animation: load5 1.1s infinite ease;
        -webkit-transform: translateZ(0);
        -ms-transform: translateZ(0);
        transform: translateZ(0);
    }
    @-webkit-keyframes load5 {
        0%,
        100% {
            box-shadow: 0em -2.6em 0em 0em #d9f9ff, 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.5), -1.8em -1.8em 0 0em rgba(217,249,255, 0.7);
        }
        12.5% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.7), 1.8em -1.8em 0 0em #d9f9ff, 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.5);
        }
        25% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.5), 1.8em -1.8em 0 0em rgba(217,249,255, 0.7), 2.5em 0em 0 0em #d9f9ff, 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        37.5% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.5), 2.5em 0em 0 0em rgba(217,249,255, 0.7), 1.75em 1.75em 0 0em #d9f9ff, 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        50% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.5), 1.75em 1.75em 0 0em rgba(217,249,255, 0.7), 0em 2.5em 0 0em #d9f9ff, -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        62.5% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.5), 0em 2.5em 0 0em rgba(217,249,255, 0.7), -1.8em 1.8em 0 0em #d9f9ff, -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        75% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.5), -1.8em 1.8em 0 0em rgba(217,249,255, 0.7), -2.6em 0em 0 0em #d9f9ff, -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        87.5% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.5), -2.6em 0em 0 0em rgba(217,249,255, 0.7), -1.8em -1.8em 0 0em #d9f9ff;
        }
    }
    @keyframes load5 {
        0%,
        100% {
            box-shadow: 0em -2.6em 0em 0em #d9f9ff, 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.5), -1.8em -1.8em 0 0em rgba(217,249,255, 0.7);
        }
        12.5% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.7), 1.8em -1.8em 0 0em #d9f9ff, 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.5);
        }
        25% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.5), 1.8em -1.8em 0 0em rgba(217,249,255, 0.7), 2.5em 0em 0 0em #d9f9ff, 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        37.5% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.5), 2.5em 0em 0 0em rgba(217,249,255, 0.7), 1.75em 1.75em 0 0em #d9f9ff, 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        50% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.5), 1.75em 1.75em 0 0em rgba(217,249,255, 0.7), 0em 2.5em 0 0em #d9f9ff, -1.8em 1.8em 0 0em rgba(217,249,255, 0.2), -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        62.5% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.5), 0em 2.5em 0 0em rgba(217,249,255, 0.7), -1.8em 1.8em 0 0em #d9f9ff, -2.6em 0em 0 0em rgba(217,249,255, 0.2), -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        75% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.5), -1.8em 1.8em 0 0em rgba(217,249,255, 0.7), -2.6em 0em 0 0em #d9f9ff, -1.8em -1.8em 0 0em rgba(217,249,255, 0.2);
        }
        87.5% {
            box-shadow: 0em -2.6em 0em 0em rgba(217,249,255, 0.2), 1.8em -1.8em 0 0em rgba(217,249,255, 0.2), 2.5em 0em 0 0em rgba(217,249,255, 0.2), 1.75em 1.75em 0 0em rgba(217,249,255, 0.2), 0em 2.5em 0 0em rgba(217,249,255, 0.2), -1.8em 1.8em 0 0em rgba(217,249,255, 0.5), -2.6em 0em 0 0em rgba(217,249,255, 0.7), -1.8em -1.8em 0 0em #d9f9ff;
        }
    }

</style>
