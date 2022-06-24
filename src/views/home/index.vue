<script setup lang="ts">
import { ref } from 'vue'
import WeekTask from '@/components/weekTask/WeekTask.vue'
import { openLink } from '@/utils'
import { weekInfo } from '@/utils/weekInfo'

const weeks = ref(weekInfo())
</script>
<template>
    <div>
        <div class="mt-4 mx-48">
            <section class="text-gray-800 mb-3">
                <div class="container mx-auto flex flex-col items-center py-12 px-4 text-center md:px-6 xl:max-w-1xl">
                    <h1 class="text-2xl font-bold leading-none sm:text-3xl">
                        <span class="text-violet-600">奥德赛 8 周任务</span>
                    </h1>
                    <div class="text-violet-600 mt-4 mb-2">( 2022年6月22日 - 2022年8月15日 )</div>
                    <p class="px-8 my-4">Arbitrum 和 Galaxy 发起的为期8周的活动。完成16个任务中的13个，将获得终极NFT。</p>
                    <!-- https://galaxy.eco/arbitrum/campaign/GCCNzUtQiW -->
                    <div class="flex flex-wrap justify-center">
                        <button
                            @click="openLink('https://twitter.com/arbitrum')"
                            class="px-6 py-2 m-2 font-semibold rounded bg-violet-600 text-gray-50"
                        >
                            项目方 Twitter
                        </button>
                        <button
                            @click="openLink('https://weibo.com/u/7664496284')"
                            class="px-6 py-2 m-2 font-semibold rounded bg-violet-600 text-gray-50"
                        >
                            Arbitrum 微博
                        </button>
                        <button
                            @click="openLink('https://twitter.com/arbitrum_cn')"
                            class="px-6 py-2 m-2 font-semibold rounded bg-violet-600 text-gray-50"
                        >
                            项目方 Twitter(中文)
                        </button>
                        <button
                            @click="openLink('https://twitter.com/mr7s1990')"
                            class="px-6 py-2 m-2 border rounded text-gray-900 border-gray-300 text-violet-600 border border-violet-600"
                        >
                            我的推特
                        </button>
                        <button
                            @click="openLink('https://weibo.com/u/7565123862')"
                            class="px-6 py-2 m-2 border rounded text-gray-900 border-gray-300 text-violet-600 border border-violet-600"
                        >
                            我的微博
                        </button>
                    </div>
                    <p class="px-8 mt-4 mb-4 text">打赏一些让开发者也可以参与项目~~</p>
                    <p class="text-violet-600">0xb5c5D73D0444048304f27624320C37b77B7A9BCF</p>
                    <div class="my-4">
                        <div class="max-w-md p-6 overflow-hidden rounded-lg shadow bg-gray-50 text-gray-800">
                            <article>
                                <button
                                    class="text-xl font-bold hover:text-violet-600 underline"
                                    @click="
                                        openLink(
                                            'https://dune.com/springzhang/arbitrum-odyssey-event-tracking?continueFlag=7af234f181d623389ccc198f346f1a40',
                                        )
                                    "
                                >
                                    Arbitrum Odyssey Dune 数据看板
                                </button>
                                <p class="mt-4 text-gray-600">
                                    Includes: Hop Protocol, Socket Bungee, Celer Network, Across Protocol, Multichain, Composable, Connext Xpollinate,
                                    Hashflow, BoringDAO, DeBridge, DeGate, Router, and Lifi Protocol. Please use the data on your own risk
                                </p>
                            </article>
                        </div>
                    </div>
                    <div class="mt-4">
                        <button
                            @click="openLink('https://chainlist.org/zh')"
                            type="button"
                            class="px-8 py-3 font-semibold border rounded border-gray-800 text-gray-800"
                        >
                            chainlist 添加 Arbitrum 网络
                        </button>
                        <button
                            @click="openLink('https://galaxy.eco/arbitrum')"
                            type="button"
                            class="px-8 py-3 ml-2 font-semibold border rounded border-gray-800 text-gray-800"
                        >
                            Galaxy Arbitrum Space
                        </button>
                    </div>
                </div>
            </section>
            <n-tabs type="segment">
                <n-tab-pane v-for="item in weeks" :key="item.key" :name="item.key">
                    <template #tab>
                        <n-badge v-if="item.status === 'expire'" dot color="grey">
                            {{ item.label }}
                        </n-badge>
                        <n-badge v-else-if="item.status === 'current'" dot processing type="success">
                            {{ item.label }}
                        </n-badge>
                        <div v-else>
                            {{ item.label }}
                        </div>
                    </template>
                    <WeekTask :weekTask="item" />
                </n-tab-pane>
            </n-tabs>
        </div>
    </div>
</template>