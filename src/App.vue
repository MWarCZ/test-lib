<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Menu />
    <div class="m-wrap">
      <div class="m-section is-limited">
        <div class="m-container">
          <h1>Lorem ipsum</h1>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis doloribus voluptatibus, vitae quod delectus assumenda quae at distinctio. Asperiores sint doloremque est odio, eveniet non! Magnam sit mollitia maiores cum!</p>
        </div>
      </div>
    </div>
    <div class="m-wrap">
      <div class="m-section is-limited">
        <progress class="m-progress" value="15" max="100">15%</progress>
        <progress class="m-progress is-primary" value="15" max="100">15%</progress>
        <progress class="m-progress is-warning" value="15" max="100">15%</progress>
        <progress class="m-progress is-danger" value="15" max="100">15%</progress>
        <div class="w-300">
          <figure class="m-image is-1by1">
            <img alt="Vue logo" src="./assets/logo.png">
          </figure>
        </div>
        <div class="w-300">
          <figure class="m-image is-4by3">
            <img alt="Vue logo" src="./assets/logo.png">
          </figure>
        </div>
        <div class="w-300">
          <figure class="m-image is-16by9">
            <img alt="Vue logo" src="./assets/logo.png">
          </figure>
        </div>
        <div class="w-300">
          <figure class="m-image is-9by16">
            <img alt="Vue logo" src="./assets/logo.png">
          </figure>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Menu from './components/Menu.vue'

export default {
  name: 'App',
  components: {
    Menu,
  }
}
</script>

<style lang="scss">

:root {
  --site-max-width: 800px;


  --light: whitesmoke;
  --light-invert: rgba(0, 0, 0, 0.8);
  --dark: #363636;
  --dark-invert: #fff;

  --primary: #00d1b2;
  --primary-invert: #fff;
  --primary-light: #ebfffc;
  --primary-dark: #00947e;

  --link: #485fc7;
  --link-invert: #fff;
  --link-light: #eff1fa;
  --link-dark: #3850b7;

  --info: #3e8ed0;
  --info-invert: #fff;
  --info-light: #eff5fb;
  --info-dark: #296fa8;

  --success: #48c78e;
  --success-invert: #fff;
  --success-light: #effaf5;
  --success-dark: #257953;

  --warning: #ffe08a;
  --warning-invert: rgba(0, 0, 0, 0.7);
  --warning-light: #fffaeb;
  --warning-dark: #946c00;

  --danger: #f14668;
  --danger-invert: #fff;
  --danger-light: #feecf0;
  --danger-dark: #cc0f35;
}

html, body {
  margin: 0;
  padding: 0;
  color: var(--light-invert);
  background-color: var(--light);
  font-size: 16px;
}
.w-300 { width: 300px; }

.m {
  &-section {
    margin-left: auto;
    margin-right: auto;

    background: rgba(255, 0, 0, 0.349);

    &.is-limited {
      max-width: var(--site-max-width);
    }
  }
  &-container {
    padding: 1rem;
  }
  &-image {
    position: relative;
    display: block;

    &.is-1by1 { padding-top: 100%; }
    // 4/5*100
    &.is-5by4 { padding-top: 80%; }
    // 3/4*100
    &.is-4by3 { padding-top: 75%; }
    // 9/16*100
    &.is-16by9 { padding-top: 56.25%; }
    // 5/4*100
    &.is-4by5 { padding-top: 125%; }
    // 4/3*100
    &.is-3by4 { padding-top: 133.3333%; }
    // 16/9*100
    &.is-9by16 { padding-top: 177.7777%; }

    &>img, &>.has-ratio {
      height: 100%;
      width: 100%;
      bottom: 0;
      left: 0;
      position: absolute;
      right: 0;
      top: 0;
    }
  }
  &-progress {
    -moz-appearance: none;
    -webkit-appearance: none;
    appearance: none;
    border: none;
    border-radius: 9999px;
    display: block;
    height: 1rem;
    overflow: hidden;
    padding: 0;
    width: 100%;
    &::-webkit-progress-bar {
      background-color: #ededed;
    }
    &::-webkit-progress-value {
      background-color: var(--bg, var(--light-invert));
    }
    &::-moz-progress-bar {
      background-color: var(--bg, var(--light-invert));
    }
    &::-ms-fill {
      background-color: var(--bg, var(--light-invert));
      border: none;
    }
  }
}

.is-light { --fg: var(--light-invert); --bg: var(--light); background-color: var(--light); color: var(--light-invert); }
.is-dark { --fg: var(--dark-invert); --bg: var(--dark); background-color: var(--dark); color: var(--dark-invert); }

.is-primary { --fg: var(--primary-invert); --bg: var(--primary); background-color: var(--primary); color: var(--primary-invert); }
.is-link { --fg: var(--link-invert); --bg: var(--link); background-color: var(--link); color: var(--link-invert); }
.is-info { --fg: var(--info-invert); --bg: var(--info); background-color: var(--info); color: var(--info-invert); }
.is-success { --fg: var(--success-invert); --bg: var(--success); background-color: var(--success); color: var(--success-invert); }
.is-warning { --fg: var(--warning-invert); --bg: var(--warning); background-color: var(--warning); color: var(--warning-invert); }
.is-danger { --fg: var(--danger-invert); --bg: var(--danger); background-color: var(--danger); color: var(--danger-invert); }

.is-light {
  &.is-primary { --fg: var(--primary-dark); --bg: var(--primary-light); background-color: var(--primary-light); color: var(--primary-dark); }
  &.is-link { --fg: var(--link-dark); --bg: var(--link-light); background-color: var(--link-light); color: var(--link-dark); }
  &.is-info { --fg: var(--info-dark); --bg: var(--info-light); background-color: var(--info-light); color: var(--info-dark); }
  &.is-success { --fg: var(--success-dark); --bg: var(--success-light); background-color: var(--success-light); color: var(--success-dark); }
  &.is-warning { --fg: var(--warning-dark); --bg: var(--warning-light); background-color: var(--warning-light); color: var(--warning-dark); }
  &.is-danger { --fg: var(--danger-dark); --bg: var(--danger-light); background-color: var(--danger-light); color: var(--danger-dark); }
}

$sm_from: 35.5em;
$md_from: 48em;
$lg_from: 64em;
$xl_from: 80em;

$sm_until: 35.4999em;
$md_until: 47.999em;
$lg_until: 63.999em;
$xl_until: 79.999em;

// OD - FROM
// sm ≥ 568px
@media screen and (min-width: $sm_from) {
  .is-hidden-from-sm { display: none; }
  img { background-color: red; }
}
// md ≥ 768px
@media screen and (min-width: $md_from) {
  .is-hidden-from-md { display: none; }
  img { background-color: orange; }
}
// lg ≥ 1024px
@media screen and (min-width: $lg_from) {
  .is-hidden-from-lg { display: none; }
  img { background-color: lime; }
}
// xl ≥ 1280px
@media screen and (min-width: $xl_from) {
  .is-hidden-from-xl { display: none; }
  img { background-color: darkgreen; }
}
// DO - UNTIL
// xl < 1280px
@media screen and (max-width: $xl_until) {
  .is-hidden-until-xl {display: none; }
  h1 { background-color: darkred; }
}
// lg < 1024px
@media screen and (max-width: $lg_until) {
  .is-hidden-until-lg {display: none; }
  h1 { background-color: purple; }
}
// md < 768px
@media screen and (max-width: $md_until) {
  .is-hidden-until-md {display: none; }
  h1 { background-color: blueviolet; }
}
// sm < 568px
@media screen and (max-width: $sm_until) {
  .is-hidden-until-sm {display: none; }
  h1 { background-color: blue; }
}



/*
Font-Size min em * 100 / break view width = font-size: ?vw
var calc_vw = (fsMin, vwMin)=>fsMin*100/vwMin
calc_vw(1,35.5)
*/
h1 {
  // font-size: clamp(1em, 4vw, 2em);
  font-size: 2.82vw;
}
// until
@media screen and (max-width: $sm_until) {
  h1 {
    font-size: 1em;
  }
}
// from
@media screen and (min-width: $lg_until) {
  h1 {
    font-size: 2em;
  }
}


</style>
<style lang="css">


</style>
