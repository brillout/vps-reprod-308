<template>
  <h1>Hello</h1>
  <p>
    Hi <b>{{ name }}</b
    >.
  </p>
  <p>{{ pageContext.pageProps.name }}</p>
  <ul>
    <li>
      <a href="/hello/eli">/hello/eli</a>
    </li>
    <li>
      <a href="/hello/jon">/hello/jon</a>
    </li>
  </ul>
  <p>
    Parameterized routes can be defined by exporting a route string in
    <code>*.page.route.js</code>.
  </p>
</template>

<script lang="ts" setup>
import {
  onActivated,
  onRenderTracked,
  onRenderTriggered,
  onUpdated,
  onServerPrefetch,
} from "vue";
import { usePageContext } from "../../renderer/usePageContext";
const props = defineProps(["name"]);
const pageContext = usePageContext();

onUpdated(() => {
  console.info("onUpdated", props, pageContext);
});

onActivated(() => {
  console.info("onActivated", props, pageContext);
});

onRenderTracked(() => {
  console.info("onRenderTracked", props, pageContext);
});

onRenderTriggered(() => {
  console.info("onRenderTriggered", props, pageContext);
});

onServerPrefetch(() => {
  console.info("onServerPrefetch", props, pageContext);
});
</script>
