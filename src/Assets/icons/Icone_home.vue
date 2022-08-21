<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    :width="size"
    :height="size"
    viewBox="0 0 32.616 27.573"
  >
    <path
      d="M11.313,27.379H3.788a1,1,0,0,1-1-1V13.464H-.338a1,1,0,0,1-.606-1.8L14.362.011a1,1,0,0,1,1.211,0L30.88,11.668a1,1,0,0,1-.606,1.8H27.147V26.378a1,1,0,0,1-1,1H18.622V20.261a1,1,0,0,0-1-1H12.314a1,1,0,0,0-1,1v7.117h0Z"
      transform="translate(1.34 0.194)"
      :fill="color[0]"
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
