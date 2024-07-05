<script lang="ts" setup>
import type { SharedCardOption } from "./shared/card";

const config: SharedCardOption = {
  datetime: "2024/07",
  title: "👋 hi 你好",
  content: `这里是一段用于HTML &lt;p&gt;标签的占位文本。在这个区域，您可以添加详细的段落内容来阐述您的观点、描述产品特性、或是提供任何您想让网站访问者阅读的信息。请记住，有效的文案应当简洁明了，同时富有吸引力，以保持读者的兴趣并引导他们进一步探索您的网站。无论是讲述一个故事，列出服务的优势，还是分享最新的行业动态，每个字句都应当精心雕琢，以传达最核心的价值。`,
  author: "Author",
  count: "字数：123",
  
  // qrcode: "",
};
</script>

<template>
  <div>
    <NuxtRouteAnnouncer />
    <SharedCard :option="config" />
  </div>
</template>
