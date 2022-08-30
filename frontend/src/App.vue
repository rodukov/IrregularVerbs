<template>
  <router-view/>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@400;500;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&display=swap');
body { margin: 0; }
input { 
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    margin: 0; 
}
input {transition: 1s;}
input::-webkit-input-placeholder { /* WebKit browsers */
    color:#0000ff;transition: 1s;
}
input::-moz-placeholder { /* Mozilla Firefox */
    color:blue;transition: 1s;
}
input:-ms-input-placeholder { /* IE 10+ */
    color:blue;transition: 1s;
}
input:focus::-webkit-input-placeholder {color:#0000ff;}
</style>
