<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .box {
    .block-default-styles();

    background-color: #fff;
    border: 1px solid rgba(0, 0, 0, 0.12);
    border-radius: 4px;

    box-shadow: 0 0 25px rgba(0, 0, 0, 0.2);

    &__inner {
      .block-default-styles();

      padding: 40px 30px 30px;

      // @media ( max-width: calc(380px + 2 * @site-paddings[small]) ) {
      //   padding: 30px 20px 20px;
      // }

      @media (max-width: 365px) {
        padding: 22px 15px 15px;
      }
    }

    &__header {
      display: block;
      width: 100%;
      margin-bottom: 20px;

      @media (max-width: 365px) {
        margin-bottom: 18px;
      }
    }

    &__title {
      .h1-text();

      margin-top: 0;
      margin-bottom: 0;

      // @media ( max-width: calc(380px + 2 * @site-paddings[small]) ) {
      //   text-align: center;
      // }

      @media (max-width: 365px) {
        font-size: 22px;
      }
    }

    &__body {
      display: block;
      width: 100%;
    }

    &__footer {
      display: block;
      width: 100%;
      margin-top: 30px;
    }

    &__item {
      margin-bottom: 10px;

      &:last-child {
        margin-bottom: 0;
      }
    }

    &__input-text {
      .h3-text();

      display: inline-block;
      vertical-align: middle;
      width: 100%;
      margin-top: 0;
      margin-bottom: 5px;
    }

    &__space-between {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
    }

    &__alternate-entry {
      display: flex;
      flex-flow: row wrap;
      justify-content: space-between;
      align-items: center;

      @media (max-width: 375px) {
        flex-direction: column;
      }
    }

    &__text {
      .body-text();

      margin-top: 0;
      margin-bottom: 0;

      line-height: 1.29;
      color: #000;

      @media (max-width: 375px) {
        margin-bottom: 10px;
      }
    }
  }
</style>

<div class="box">
  <div class="box__inner">
    <div class="box__header">
      <h2 class="box__title">
        <slot name="title"></slot>
      </h2>
    </div>
    <div class="box__body">
      <slot></slot>
    </div>
    <div class="box__footer">
      <slot name="footer"></slot>
    </div>
  </div>
</div>
