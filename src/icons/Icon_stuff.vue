<template>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width="23"
    height="23"
    viewBox="0 0 24.502 24.502"
  >
    <path
      d="M22.752,2.25h-21A1.75,1.75,0,0,0,0,4V25a1.75,1.75,0,0,0,1.75,1.75h21A1.75,1.75,0,0,0,24.5,25V4A1.75,1.75,0,0,0,22.752,2.25ZM21,5.75v7H14v-7Zm-10.5,0v7h-7v-7Zm-7,17.5v-7h7v7Zm10.5,0v-7h7v7Z"
      transform="translate(0 -2.25)"
      :fill="color[2]"
    />
  </svg>
</template>

<script>
export default {
  props: {
    color: [],
  },
};
</script>

<style></style>
