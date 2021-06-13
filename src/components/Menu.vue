<template>
  <header class="menu-wrap">
    <input type="checkbox" class="menu-checkbox" id="menu-checkbox">
    <div class="header">
      <label for="menu-checkbox" class="menu-toggle">
      </label>
    </div>
    <nav class="menu">
      <ul class="menu-list">
        <li><a href="#"><span>xxx</span></a></li>
        <li><a href="#"><span>xxx</span></a></li>
        <li class="with-submenu">
          <a href="#"><span>xxx</span></a>
          <ul class="menu-list is-submenu">
            <li><a href="#"><span>yyy</span></a></li>
            <li><a href="#"><span>yyy</span></a></li>
          </ul>
        </li>
      </ul>
    </nav>

  </header>
</template>
<script>
export default {

}
</script>
<style lang="scss">
  .menu-wrap {
    --line-height: .1em;
    --border-radius: .1em;
  }
  // Input
  .menu-checkbox {
    position: absolute;
    z-index: -999;
    left: -900vw;
  }

  // Button toggle
  .menu-toggle {
    display: block;
    font-size: 4em;
    height: .7em;
    width: .7em;
    margin-top: .1em;
    margin-left: 0;
    transform: none;
    overflow: hidden;
  }
  .menu-toggle::after,
  .menu-toggle::before {
    content: "";
    width: 80%;
    height: .1em;
    height: var(--line-height);
    display: block;
    margin: .1em auto;
    margin: var(--line-height) auto;
    border-radius: var(--border-radius);
    background-color: currentColor;
    transition: transform, box-shadow;
    transition-duration: 200ms;
    transition-timing-function: ease-in-out;
  }
  .menu-toggle::before {
    margin-bottom: calc(var(--line-height) * 3);
    box-shadow: currentColor 0 calc(var(--line-height) * 2);
  }
  // Button toggle opened
  .menu-checkbox:checked ~ * .menu-toggle::before {
    transform: translateY(0.2em) rotate(135deg);
    box-shadow: transparent 0 0;
  }
  .menu-checkbox:checked ~ * .menu-toggle::after {
    transform: translateY(-0.2em) rotate(-135deg);
  }
  // List closed
  .menu {
    max-height: 0;
    visibility: hidden;
    font-size: 1.3em;
  }
  // List opened
  .menu-checkbox:checked ~ .menu,
  .menu-checkbox:checked ~ * .menu {
    max-height: unset;
    visibility: visible;
  }


  :root {
    --menu-fg: #000;
    --menu-fg-hover: #333;

    --menu-bg: #fff;
    --menu-bg-hover: #fff9f0;

    --submenu-fg: #bc8c42;
    --submenu-bg: #faedda;

    --submenu-line-color: #e4d1b1;
  }
  .menu-list {
    list-style: none;
    padding: 0;
    margin: 0;
    color: var(--menu-fg);
    background-color: var(--menu-bg);

    > li {
      display: inline-block;
      position: relative;
      transition: 0.25s background-color, 0.25s color;
      &:hover, &:focus-within {
        color: var(--menu-fg-hover);
        background-color: var(--menu-bg-hover);
        .is-submenu {
          visibility: visible;
        }
      }
    }
    a {
      display: block;
      text-decoration: none;
      padding: .5rem 1.25rem;
      font-size: 1em;
      color: inherit;
    }
    .with-submenu > a::after {
      content: "";
      border: 0.1em solid currentColor;
      display: inline-block;
      height: 0.4em;
      width: 0.4em;
      box-sizing: border-box;
      transform: translateY(-25%) rotate(45deg);
      border-top: none;
      border-left: none;
      margin-left: 0.25em;
    }

    &.is-submenu {
      display: flex;
      flex-direction: column;
      position: absolute;
      color: var(--submenu-fg);
      background-color: var(--submenu-bg);
      visibility: hidden;
      > * + * a::after {
        border-top: 1px solid var(--submenu-line-color);
        content: '';
        display: block;
        position: absolute;
        width: calc(100% - 2rem);
        top: 0;
      }
    }
  }


  $sm_from: 35.5em;
  $md_from: 48em;
  $lg_from: 64em;
  $xl_from: 80em;

  $sm_until: 35.4999em;
  $md_until: 47.999em;
  $lg_until: 63.999em;
  $xl_until: 79.999em;
  // md < 768px
  @media screen and (max-width: $md_until) {
    .menu-list {
      > li {
        display: block;
        &:not(:last-child) > a::after  {
          border-top: 1px solid var(--submenu-line-color);
          content: '';
          display: block;
          position: absolute;
          width: calc(100% - 2rem);
          bottom: 0;
        }
      }
      &.is-submenu {
        position: static;
        visibility: inherit;
        li a::before {
          content: "›";
          display: inline-block;
          padding: 0 .5em;
        }
      }
    }
  }

// md ≥ 768px
@media screen and (min-width: $md_from) {
  .menu-toggle { display: none; }
}

</style>
