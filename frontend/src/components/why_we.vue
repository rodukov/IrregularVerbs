<template>
<div class="why_we">
    <div class="text_container">
        <p class="one">What is the essence of the project?</p>
        <p class="two">
            A project that allows you to train your knowledge of irregular verbs in English.
            The essence of the project, a random verb is selected and you must remember the
            second and third forms for it. Shows  errors. You can choose the level of difficulty.
            There are 604 irregular verbs in English. However, the easy difficulty level will only produce the 100 most used.
        </p>
    </div>
    <div class="main_container">
        <div class="main">
            <h3 class="s" style="text-align: center;">S1mple</h3>
            <h2 class="m" style="text-align: center;">Lorem Ipsum is simply dummy text of the printing and typesetting industry.</h2>
        </div>
        <div class="main">
            <h3 class="s" style="text-align: center;">S1mple</h3>
            <h2 class="m" style="text-align: center;">Lorem Ipsum is simply dummy text of the printing and typesetting industry.</h2>
        </div>
        <div class="main">
            <h3 class="s" style="text-align: center;">S1mple</h3>
            <h2 class="m" style="text-align: center;">Lorem Ipsum is simply dummy text of the printing and typesetting industry.</h2>
        </div>
    </div>

</div>
</template>

<script>
export default {
    name: 'why_we'
}    
</script>

<style>
.one {
    font-family: 'Merriweather';
    font-size: 20px;
    font-weight: 700;
}
.two {
    font-family: 'Merriweather';
    font-size: 27px;
    font-weight: 500;
}
.why_we {
    display: flex;
    margin-top: 20px;
}
.text_container {
    width: 50%;
    padding-left: 25px;
    padding-right: 25px;
    margin-left: 15px;
    margin-right: 15px;
    border-radius: 3px;
    text-align: justify;
    background: white;
    box-shadow: 0px 3px 15px rgba(226, 226, 226, 0.726);
}
.main_container {
    width: 50%;
    margin-right: 15px;
}
.main {
    display: inline-block;
    background: blue;
    width: 100%;
}
.m {
    font-family: arial;
}
.s {
    font-family: arial;
}
</style>