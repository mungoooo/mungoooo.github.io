<script>
  import 'vidstack/bundle';
  import 'vidstack/icons';
  const { title, src } = $props();
</script>

<div class="font-serif">
  <media-player {title} {src}>
    <media-provider></media-provider>
    <media-audio-layout></media-audio-layout>
  </media-player>
</div>
