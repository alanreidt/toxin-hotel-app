<script>
  import "../node_modules/flatpickr/dist/flatpickr.css";
  import "../node_modules/nouislider/distribute/nouislider.min.css";
  import "./styles/global.less";

  import Datepicker from "./components/Datepicker.svelte";
  import InputField from "./components/InputField.svelte";
  import DateInputField from "./components/DateInputField.svelte";
  import Dropdown from "./components/Dropdown.svelte";
  import DateDropdown from "./components/DateDropdown.svelte";
  import FilterDateDropdown from "./components/FilterDateDropdown.svelte";
  import SubscriptionField from "./components/SubscriptionField.svelte";
  import Checkbox from "./components/Checkbox.svelte";
  import StatefulInput from "./components/StatefulInput.svelte";
  import RadioButton from "./components/RadioButton.svelte";
  import Toggle from "./components/Toggle.svelte";
  import LikeButton from "./components/LikeButton.svelte";
  import Rating from "./components/Rating.svelte";
  import BulletList from "./components/BulletList.svelte";
  import CellBlock from "./components/CellBlock.svelte";
  import Comment from "./components/Comment.svelte";
  import Pagination from "./components/Pagination.svelte";
  import Button from "./components/Button.svelte";
  import SearchBox from "./components/SearchBox.svelte";
  import RegistrationBox from "./components/RegistrationBox.svelte";
  import CalculationBox from "./components/CalculationBox.svelte";
  import EntryBox from "./components/EntryBox.svelte";
  import RoomBox from "./components/RoomBox.svelte";
  import Topline from "./components/Topline.svelte";
  import Footer from "./components/Footer.svelte";
  import RangeSlider from "./components/RangeSlider.svelte";

  const dropdownOptions = [
    { name: "Взрослые", min: 0, max: 5, value: 0 },
    { name: "Дети", min: 0, max: 5, value: 0 },
    { name: "Младенцы", min: 0, max: 3, value: 0 },
  ];

  const checkboxOptions = [
    {
      labelText: "Можно курить",
      value: "smoke",
    },
    {
      labelText: "Можно с&nbsp;питомцами",
      value: "pets",
    },
    {
      labelText: "Можно пригласить гостей (до&nbsp;10&nbsp;человек)",
      value: "guests",
    },
  ];

  const radioButtonOptions = [
    { labelText: "Мужчина", value: "man", checked: true },
    { labelText: "Женщина", value: "woman", checked: false },
  ];

  const richCheckboxOptions = [
    {
      labelText: "Широкий коридор",
      labelExplanation:
        "Ширина коридоров в&nbsp;номере не&nbsp;менее 91&nbsp;см.",
      value: "wide-corridor",
    },
    {
      labelText: "Помощник для инвалидов",
      labelExplanation:
        "На&nbsp;1&nbsp;этаже вас встретит специалист и&nbsp;проводит до&nbsp;номера.",
      value: "assistant",
    },
  ];

  const bulletListItems = [
    "Нельзя с&nbsp;питомцами",
    "Без вечеринок и&nbsp;мероприятий",
    "Время прибытия&nbsp;&mdash; после 13:00, а&nbsp;выезд до&nbsp;12:00",
  ];

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
</script>

<style lang="less">
  .row {
    display: block;
    width: 100%;

    &_small {
      max-width: 320px;
    }

    &_medium {
      max-width: 380px;
    }

    &_large {
      max-width: 712px;
    }
  }
</style>

<main>
  <div class="row row_small">
    <InputField name="text-field" labelText="text field" placeholder="Email" />
    <DateInputField name="date-text-field" labelText="masked text field" />
    <Dropdown
      labelText="Dropdown"
      options={dropdownOptions}
      hasButtonPane={true}
      name="dropdown-input" />
    <DateDropdown />
    <FilterDateDropdown />
    <SubscriptionField labelText="subscription text field" />
    {#each checkboxOptions as option}
      <Checkbox {...option} name="permission" />
    {/each}
    {#each richCheckboxOptions as option}
      <Checkbox {...option} name="accesibility" />
    {/each}
    {#each radioButtonOptions as option}
      <RadioButton {...option} name="sex" />
    {/each}
    <Toggle
      labelText="Получать спецпредложения"
      name="mailing" />
    <LikeButton
      labelText="Нравится"
      name="liked"
      dataValue="12" />
    <Rating id="rating" name="rating" />
    <Rating id="rating-readonly" name="rating-readonly" rating="3" />
    <BulletList items={bulletListItems} />
    <CellBlock options={cellBlockOptions} />
    <Pagination />

    <Button text="click me" mods="main" href="#" />
    <Button text="click me" mods="secondary" href="#" />
    <Button text="click me" href="#" />
    <Button text="click me" mods="reset" href="#" />
    <Button text="перейти к оплате" mods="full-width" />

    <RangeSlider />
  </div>
  <div class="row row_large">
    {#each commentOptions as option}
      <Comment {...option} />
    {/each}
  </div>
  <div class="row row_medium">
    <SearchBox />
    <RegistrationBox />
    <CalculationBox />
    <EntryBox />
    <RoomBox />
  </div>
  <div class="row">
    <Topline />
    <Footer />
  </div>
</main>
