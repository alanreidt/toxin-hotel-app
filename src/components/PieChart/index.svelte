<script>
  let captionsList = document.querySelectorAll('.caption-item');
  let unitsList = document.querySelectorAll('.unit');

  captionsList.forEach(function (item, index) {
    item.addEventListener('mouseover', function () {
      unitsList[index].classList.add('hovered');
    });

    item.addEventListener('mouseout', function () {
      unitsList[index].classList.remove('hovered');
    });
  });
</script>

<style lang="less">
  @import "../../styles/variables";
  @import "../../styles/mixins";

  @keyframes render {
    0% {
      stroke-dasharray: 0 100;
    }
  }

  .canvas {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    max-width: 500px;
  }

  .legend {
    max-width: 250px;
    margin-left: 30px;
  }

  .caption-list {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  .caption-item {
    position: relative;

    margin: 20px 0;
    padding-left: 30px;

    font-family: "Verdana", sans-serif;
    font-size: 16px;
    line-height: 18px;
    color: #591d48;
    cursor: pointer;
  }

  .caption-item:hover {
    opacity: 0.8;
  }

  .caption-item::before {
    content: "";

    position: absolute;
    top: 0;
    left: 0;

    width: 20px;
    height: 20px;

    border-radius: 8px;
  }

  .caption-item:nth-child(1)::before {
    background-image: linear-gradient(180deg, #FFE39C 0%, #FFBA9C 100%);
  }

  .caption-item:nth-child(2)::before {
    background-image: linear-gradient(180deg, #6FCF97 0%, #66D2EA 100%);
  }

  .caption-item:nth-child(3)::before {
    background-image: linear-gradient(180deg, #BC9CFF 0%, #8BA4F9 100%);
  }

  .caption-item:nth-child(4)::before {
    background-image: linear-gradient(180deg, #919191 0%, #3D4975 100%);
  }

  .chart {
    min-width: 100px;
    transform: rotate(90deg);
  }

  .unit {
    fill: none;
    stroke-width: 1;
    cursor: pointer;

    animation-name: render;
    animation-duration: 1.5s;
    transition-property: all;
    transition-duration: 1.5s;
  }

  .unit:hover,
  .hovered {
    opacity: 0.8;
    stroke-width: 2;
  }

  .unit:nth-child(1) {
    stroke: #FFE39C;
    stroke-dasharray: 50 100;
  }

  .unit:nth-child(2) {
    stroke: #6FCF97;
    stroke-dasharray: 25 100;
    stroke-dashoffset: -50;
  }

  .unit:nth-child(3) {
    stroke: #BC9CFF;
    stroke-dasharray: 23 100;
    stroke-dashoffset: -75;
  }

  .unit:nth-child(4) {
    stroke: #919191;
    stroke-dasharray: 2 100;
    stroke-dashoffset: -98;
  }
</style>

<div class="canvas">
  <svg class="chart" width="120" height="120" viewBox="0 0 33 33" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="excellent" gradientTransform="rotate(180)">
        <stop offset="0%"   stop-color="#FFE39C" />
        <stop offset="100%" stop-color="#FFBA9C" />
      </linearGradient>
      <linearGradient id="good" gradientTransform="rotate(180)">
        <stop offset="0%"   stop-color="#6FCF97" />
        <stop offset="100%" stop-color="#66D2EA" />
      </linearGradient>
      <linearGradient id="normal" gradientTransform="rotate(180)">
        <stop offset="0%"   stop-color="#BC9CFF" />
        <stop offset="100%" stop-color="#8BA4F9" />
      </linearGradient>
      <linearGradient id="bad" gradientTransform="rotate(180)">
        <stop offset="0%"   stop-color="#919191" />
        <stop offset="100%" stop-color="#3D4975" />
      </linearGradient>
    </defs>

    <circle class="unit" stroke="url(#excellent)" r="15.9" cx="50%" cy="50%" />
    <circle class="unit" stroke="url(#good)" r="15.9" cx="50%" cy="50%" />
    <circle class="unit" stroke="url(#normal)" r="15.9" cx="50%" cy="50%" />
    <circle class="unit" stroke="url(#bad)" r="15.9" cx="50%" cy="50%" />
  </svg>

  <div class="legend">
    <ul class="caption-list">
      <li class="caption-item">Великолепно</li>
      <li class="caption-item">Хорошо</li>
      <li class="caption-item">Удовлетворительно</li>
      <li class="caption-item">Разочарован</li>
    </ul>
  </div>
</div>
