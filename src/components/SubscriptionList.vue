<template>

    <section class="subscription-list">
        <div class="subscription-addition-box">
            <div class="field">
                <label class="label"
                       for="subscriptionSearch">
                    Enter RSS Feed URL
                </label>
                <div class="control has-icons-left">
                    <input class="input is-info is-rounded"
                           id="subscriptionSearch"
                           placeholder="Search..."
                           type="text"
                           v-model="feedUrl"
                           @keyup.enter="subscribeToUrl(feedUrl)"/>
                    <span class="icon is-small is-left">
                        <i class="fas fa-search"></i>
                    </span>
                </div>
            </div>
            <div class="field is-grouped">
                <div class="control">
                    <button class="button is-link"
                            @click="subscribeToUrl(feedUrl)">
                        Submit
                    </button>
                </div>
                <div class="control">
                    <button class="button is-link is-light"
                            @click="clearSearchBar()">
                        Clear
                    </button>
                </div>
            </div>
        </div>
        <div class="user-subscriptions-list">
            <div v-for="(subscription, index) in subscriptions" :key="index"
                 :class="{ 'card-active': isActiveSubscription(subscription) }"
                 class="card">
                <div class="card-content">
                    <div class="field ellipsis"
                         :title="subscription">
                        URL: {{subscription}}
                    </div>
                    <div class="field is-grouped">
                        <div class="control">
                            <button class="button is-link"
                                    @click="setActiveSubscription(subscription)"
                                    :disabled="isActiveSubscription(subscription)">
                                Activate
                            </button>
                        </div>
                        <div class="control">
                            <button class="button is-link is-light"
                                    @click="unsubscribeToUrl(index)">
                                Remove
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

</template>

<script>
    export default {
        name: 'SubscriptionList',
        props: [],
        created() {
            this.initializeSubscriptions();
        },
        data() {
            return {
                subscriptions: [],
                activeSubscription: '',
                feedUrl: ''
            };
        },
        methods: {
            initializeSubscriptions() {
                this.subscriptions = [];
                this.subscribeToUrl("https://rss.app/feeds/6z49rlYEY9A58Me4.xml");
                this.subscribeToUrl("https://rss.app/feeds/wG3QpBBx5UsKUO7L.xml");
            },
            subscribeToUrl(url) {
                if (!url || this.subscriptions.indexOf(url) !== -1) {
                    return;
                }
                this.subscriptions.push(url);
                this.setActiveSubscription(url);
                this.clearSearchBar();
            },
            unsubscribeToUrl(index) {
                if (this.subscriptions[index] === this.activeSubscription) {
                    this.setActiveSubscription();
                }
                this.subscriptions.splice(index, 1);
            },
            setActiveSubscription(url) {
                this.activeSubscription = url;
                this.$emit('change-active-subscription', this.activeSubscription);
            },
            isActiveSubscription(url) {
                return (this.activeSubscription === url);
            },
            clearSearchBar() {
                this.feedUrl = '';
            }
        },
        computed: {}
    }
</script>

<style scoped lang="scss">
    $subscription-addition-box-height: 165px;

    .subscription-list {
        width: 100%;
    }

    .subscription-addition-box {
        padding: 20px 30px;
        border-bottom: 1px dashed black;
        height: $subscription-addition-box-height;
    }

    .user-subscriptions-list {
        height: calc(100vh - #{$subscription-addition-box-height});
        overflow-y: auto;
        padding: 20px
    }

    .card:not(:last-child) {
        margin-bottom: 10px;
    }

    .card-active {
        background: #d9f9ff;
    }
</style>
