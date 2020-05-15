<script>
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
      <li class="socials__item">
        <a
          class="socials__link"
          href="change-me"
          target="_blank"
          title="twitter"
          aria-label="twitter">
          <svg class="socials__icon" width="24" height="24" alt="twitter">
            <use
              href="../../blocks/common.blocks/socials/images/socials__icon_tw.svg" />
          </svg>
        </a>
      </li>
      <li class="socials__item">
        <a
          class="socials__link"
          href="change-me"
          target="_blank"
          title="facebook"
          aria-label="facebook">
          <svg class="socials__icon" width="24" height="24" alt="facebook">
            <use
              href="../../blocks/common.blocks/socials/images/socials__icon_fb.svg" />
          </svg>
        </a>
      </li>
      <li class="socials__item">
        <a
          class="socials__link"
          href="change-me"
          target="_blank"
          title="instagram"
          aria-label="instagram">
          <svg class="socials__icon" width="24" height="24" alt="instagram">
            <use
              href="../../blocks/common.blocks/socials/images/socials__icon_ig.svg" />
          </svg>
        </a>
      </li>
    </ul>
  </div>
</div>
