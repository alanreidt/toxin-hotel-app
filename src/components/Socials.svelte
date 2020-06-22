<script>
  export let optionsList = [
    { name: "twitter", href: "/mock-address/change-me", src: "/images/twitter-social-icon.svg", },
    { name: "facebook", href: "/mock-address/change-me", src: "/images/facebook-social-icon.svg", },
    { name: "instagram", href: "/mock-address/change-me", src: "/images/instagram-social-icon.svg", },
  ];
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .socials {
    &__inner {
      .block-default-styles();
    }

    &__list {
      .list-styles-reset();

      display: flex;
      flex-flow: row nowrap;
    }

    &__item {
      display: inline-block;
      vertical-align: middle;
      margin-right: 20px;

      &:last-child {
        margin-right: 0;
      }
    }

    &__link {
      text-decoration: none;

      display: inline-block;
      vertical-align: middle;

      &:hover,
      &:focus {
        opacity: 0.5;
      }
    }

    &__icon {
      display: inline-block;
      vertical-align: middle;
      width: 24px;
      height: 24px;
    }
  }
</style>

<div class="socials">
  <div class="socials__inner">
    <ul class="socials__list">
      {#each optionsList as {name, href, src}}
        <li class="socials__item">
          <a
            class="socials__link"
            {href}
            target="_blank"
            rel="noopener noreferrer"
            title={name}
            aria-label={name}>
            <img {src} alt="{name} icon" class="socials__icon" width="24" height="24">
          </a>
        </li>
      {/each}
    </ul>
  </div>
</div>
