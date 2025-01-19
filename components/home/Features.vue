<script setup>
import { AreaChart, Hourglass, Link, Paintbrush, ServerOff, Sparkles } from 'lucide-vue-next'

const features = ref([
  {
    title: '链接缩短',
    description:
          '将您的链接压缩到最小长度。',
    icon: Link,
  },
  {
    title: '数据分析',
    description:
          '自动分析您的链接的访问情况。',
    icon: AreaChart,
  },
  {
    title: '无服务器',
    description:
          '无需传统服务器即可部署。',
    icon: ServerOff,
  },
  {
    title: '自定义 Slug',
    description:
          '支持自定义Slug并支持区分大小写。',
    icon: Paintbrush,
  },
  {
    title: 'AI Slug',
    description:
          '使用Workers AI自动生成Slug。',
    icon: Sparkles,
  },
  {
    title: '时间设定',
    description:
          '为您的链接设置过期时间。',
    icon: Hourglass,
  },
])
</script>

<template>
  <main class="pt-16 md:py-12">
    <div class="md:pb-12">
      <h2 class="text-4xl font-bold lg:text-5xl lg:tracking-tight">
        功能
      </h2>
      <p class="my-8 text-lg md:mb-0 text-slate-600">
        简单、实用、方便的功能
      </p>
    </div>

    <div class="grid gap-8 md:gap-16 sm:grid-cols-2 md:grid-cols-3">
      <div
        v-for="item in features"
        :key="item.title"
        class="flex items-start gap-4"
      >
        <div class="w-8 h-8 p-2 mt-1 bg-black rounded-full shrink-0">
          <component
            :is="item.icon"
            class="w-4 h-4 text-white"
          />
        </div>
        <div>
          <h3 class="text-lg font-semibold">
            {{ item.title }}
          </h3>
          <p class="mt-2 leading-relaxed text-slate-500">
            {{ item.description }}
          </p>
        </div>
      </div>
    </div>
  </main>
</template>
