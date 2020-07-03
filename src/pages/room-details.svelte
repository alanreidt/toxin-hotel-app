<script>
  import RoomDetailsHead from "../components/RoomDetailsHead.svelte";
  import RoomDetailsBody from "../components/RoomDetailsBody.svelte";

  import { metatags } from '@sveltech/routify';

  metatags.title = "change-me";
  metatags.description = "change-me";
</script>

<!-- routify:options name="room-details" index=false -->

<div class="room-details">
  <div class="room-details__head">
    <RoomDetailsHead />
  </div>
  <div class="room-details__body">
    <RoomDetailsBody />
  </div>
</div>
