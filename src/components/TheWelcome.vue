<script setup>
import WelcomeItem from "./WelcomeItem.vue";
import DocumentationIcon from "./icons/IconDocumentation.vue";
import CommunityIcon from "./icons/IconCommunity.vue";
import SupportIcon from "./icons/IconSupport.vue";
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>How to use</template>

    FPS detector run
    <a
      target="_blank"
      href="https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame"
    >
      requestAnimationFrame()
    </a>
    to detect the current FPS in the browser.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>Community</template>

    Real geeks needs highest fps not only from hardware, but also software.
    <a target="_blank" href="https://www.google.com/chrome/">Chrome</a> usually
    render at 60 fps, but it is
    <a
      target="_blank"
      href="https://dev.to/uwutrinket/chrome-unlimited-frame-rate-gl2"
      >improvable</a
    >. Please follow the official
    <a target="_blank" href="https://twitter.com/fpsgeek240">fps geek</a>
    twitter account for latest fps tricks.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Support FPS geek</template>

    FPS geek relies on community backing for its sustainability. You can help
    fps geek by becoming a sponsor.
  </WelcomeItem>
</template>
