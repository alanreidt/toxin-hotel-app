<script>
  import wNumb from 'wnumb';
  import noUiSlider from 'nouislider';

  let rangeSliderOutput = document.getElementById('js-range-slider__output');
  let rangeSliderValues;
  let rangeSliderRange = '';
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

    // rangeSlider.noUiSlider.on('update', function () {
    //   rangeSliderValues = rangeSlider.noUiSlider.get();

    //   rangeSliderRange = rangeSliderValues[0] + '–' + rangeSliderValues[1];

    //   rangeSliderOutput.innerHTML = rangeSliderRange;
    // });

    return {
      update: (newOptions) => null,
      destroy: () => rangeSlider.noUiSlider.destroy(),
    };
  }
</script>

<style lang="less">
  @import "../styles/variables";
  @import "../styles/mixins";

  @range-slider-handle-width: 12px;

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

  .range-slider__input {
    background-color: #fff;
    // change to dark-shade-25 later
    border: 1px solid #colors[dark-shade-50];
    border-radius: 3px;
    box-shadow: none;

    :global(&.noUi-horizontal) {
      height: 6px;
    }

    :global(& .noUi-connect) {
      background-image: @secondary-gradient;
    }

    :global(&.noUi-horizontal .noUi-handle) {
      // find generic value
      top: -4px;
      width: @range-slider-handle-width;
      height: @range-slider-handle-width;
    }

    :global(& .noUi-handle) {
      background-image: @secondary-gradient;
      border: 2px solid #fff;
      border-radius: 50%;
      box-shadow: none;

    }

    :global(& .noUi-handle::before),
    :global(& .noUi-handle::after) {
      display: none;
    }
  }

  :global(html:not([dir="rtl"]) .noUi-horizontal .noUi-handle) {
    right: -1 * @range-slider-handle-width / 2;
  }
</style>

<div class="range-slider">
  <div class="range-slider__header">
    <span class="range-slider__title">диапазон цен</span>
    <span class="range-slider__output" id="js-range-slider__output">
      1 000₽–15 000₽
    </span>
  </div>
  <div use:noUiSliderInit={noUiSliderOptions} class="range-slider__input" id="js-range-slider__input"></div>
  <p class="range-slider__explanation">
    Стоимость за&nbsp;сутки пребывания в&nbsp;номере
  </p>
  <div class="noUi-base"></div>
</div>
