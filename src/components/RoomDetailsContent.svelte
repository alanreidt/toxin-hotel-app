<script>
  import CellBlock from "./CellBlock.svelte";
  import BulletList from "./BulletList.svelte";
  import Comment from "./Comment.svelte";

  const cellBlockOptions = [
    {
      title: "Комфорт",
      description: "Шумопоглощающие стены",
      materialIconName: "insert_emoticon",
    },
    {
      title: "Удобство",
      description: "Окно в&nbsp;каждой из&nbsp;спален",
      materialIconName: "location_city",
    },
    {
      title: "Уют",
      description: "Номер оснащен камином",
      materialIconName: "whatshot",
    },
  ];

  const commentOptions = [
    {
      authorName: "Мурад Сарафанов",
      date: "5 дней назад",
      imgSrc: "/images/man.png",
      liked: true,
      likeButtonValue: 12,
      commentText:
        "Великолепный матрас на&nbsp;кровати в&nbsp;основной спальне! А&nbsp;пуфик вообще потрясающий. И&nbsp;стены, действительно, шумоподавляющие. Выкрикивал комплименты повару&nbsp;&mdash; никто не&nbsp;жаловался из&nbsp;соседей.",
    },
    {
      authorName: "Патрисия Стёклышкова",
      date: "неделю назад",
      imgSrc: "/images/girl.png",
      liked: false,
      likeButtonValue: 9,
      commentText:
        "Обслуживание на&nbsp;высоте! Всё аккуратно, чисто. Завтраки в&nbsp;номер советую заказать, каждый день новое блюдо и&nbsp;десерт как комплимент",
    },
  ];

  const bulletListItems = [
    "Нельзя с&nbsp;питомцами",
    "Без вечеринок и&nbsp;мероприятий",
    "Время прибытия&nbsp;&mdash; после 13:00, а&nbsp;выезд до&nbsp;12:00",
  ];
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .room-details-content {
    .block-default-styles();
    padding-right: 8%;

    &__inner {
      .block-default-styles();

      display: grid;
      grid-template-columns: 304px 360px;
      grid-gap: 30px 40px;
      justify-content: space-between;
    }

    &__comment-section {
      grid-column: ~"1 / 3";
    }

    &__section-header {
      display: flex;
      flex-flow: row wrap;
      justify-content: space-between;
      align-items: baseline;
    }

    &__section-title {
      .h2-text();

      display: inline-block;
      vertical-align: middle;

      margin-top: 0;
      margin-bottom: 20px;
    }

    &__section-sub-title {
      .body-text();

      line-height: 1;
      color: #colors[dark-shade-50];
    }

    &__section-text {
      .body-text();

      margin-top: 0;
      margin-bottom: 0;
    }
  }
</style>

<div class="room-details-content">
  <div class="room-details-content__inner">
    <div class="room-details-content__section">
      <span class="room-details-content__section-title">Сведения о номере</span>
      <div class="room-details-content__section-content">
        <CellBlock options={cellBlockOptions} />
      </div>
    </div>
    <div class="room-details-content__section">
      <span class="room-details-content__section-title">
        Впечатления от номера
      </span>
      <div class="room-details-content__section-content">
        <!-- pie-chart -->
      </div>
    </div>
    <div
      class="room-details-content__section room-details-content__comment-section">
      <div class="room-details-content__section-header">
        <span class="room-details-content__section-title">
          Отзывы посетителей номера
        </span>
        <span class="room-details-content__section-sub-title">
          {commentOptions.length} {commentOptions.length === 1 ? "отзыв" : "отзыва"}
        </span>
      </div>
      <div class="room-details-content__section-content">
        {#each commentOptions as option}
          <Comment {...option} />
        {/each}
      </div>
    </div>
    <div class="room-details-content__section">
      <span class="room-details-content__section-title">Правила</span>
      <div class="room-details-content__section-content">
        <BulletList items={bulletListItems} />
      </div>
    </div>
    <div class="room-details-content__section">
      <span class="room-details-content__section-title">Отмена</span>
      <div class="room-details-content__section-content">
        <p class="room-details-content__section-text">
          Бесплатная отмена в&nbsp;течение 48&nbsp;ч. После этого при отмене
          не&nbsp;позднее чем за&nbsp;5&nbsp;дн.&nbsp;до&nbsp;прибытия
          вы&nbsp;получите полный возврат за&nbsp;вычетом сбора за&nbsp;услуги.
        </p>
      </div>
    </div>
  </div>
</div>
