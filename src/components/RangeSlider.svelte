<script>
  import wNumb from 'wnumb';
  import noUiSlider from 'nouislider';

  let output;
  let values = [];
  $: range = values[0] + ' – ' + values[1];

  const noUiSliderOptions = {
    start: [5000, 10000],
    step: 500,
    margin: 500,
    connect: true,
    range: {
      'min': 0,
      'max': 15000
    },
    ariaFormat: wNumb({
      decimals: 0
    }),
    format: wNumb({
      decimals: 0,
      thousand: ' ',
      suffix: '₽'
    })
  };

  function noUiSliderInit(node, options) {
    const rangeSlider = noUiSlider.create(node, options);

    rangeSlider.on('update', function () {
      values = rangeSlider.get();
    });

    return {
      destroy: () => rangeSlider.destroy(),
    };
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  .range-slider {
    &__header {
      display: flex;
      flex-direction: row;
      flex-wrap: nowrap;
      justify-content: space-between;

      margin-bottom: 20px;
    }

    &__title {
      .h3-text();

      display: inline-block;
      vertical-align: center;
      margin-top: 0;
      margin-bottom: 0;
    }

    &__output {
      .h3-text();

      margin-top: 0;
      margin-bottom: 0;

      font-weight: 400;
      color: #colors[dark-shade-50];
    }

    &__explanation {
      .body-text();

      margin-top: 10px;
      margin-bottom: 0;

      font-size: 12px;
      line-height: 1.17;
      color: #colors[dark-shade-50];
    }
  }
</style>

<div class="range-slider">
  <div class="range-slider__header">
    <span class="range-slider__title">диапазон цен</span>
    <span bind:this={output} class="range-slider__output">
      {range}
    </span>
  </div>
  <div use:noUiSliderInit={noUiSliderOptions} class="range-slider__input"></div>
  <p class="range-slider__explanation">
    Стоимость за&nbsp;сутки пребывания в&nbsp;номере
  </p>
</div>
