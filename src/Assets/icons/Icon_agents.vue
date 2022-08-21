<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    :width="size"
    :height="size"
    viewBox="0 0 22.487 22.487"
  >
    <path
      d="M15.744,15.744a5.622,5.622,0,1,0-5.622-5.622A5.638,5.638,0,0,0,15.744,15.744Zm0,2.811c-3.724,0-11.244,1.9-11.244,5.622v2.811H26.987V24.176C26.987,20.452,19.468,18.554,15.744,18.554Z"
      transform="translate(-4.5 -4.5)"
      :fill="color[4]"
    />
  </svg>
</template>

<script>
export default {
  props: {
    color: "",
    size: "",
  },
};
</script>

<style></style>
