<script>
  import Audio from '../../components/Audio.svelte';
</script>

<div class="no-full-padding flex flex-col">
  <div class="relative flex flex-grow flex-col">
    <main
      class="mainminh full-padding2 flex flex-grow flex-col pt-[200px] sm:pt-[12px] md:ml-[150px]"
    >
      <section
        class="full-work-padding mx-auto flex w-full max-w-[2000px] flex-col overflow-y-hidden pt-[20px] leading-relaxed [word-spacing:0.1rem] md:space-y-8 md:p-12"
      >
        <div class="mainminh-poster relative md:grid md:grid-cols-2">
          <div class="mainminh-poster h-full">
            <img
              src="/assets/images/embed/balladposter.webp"
              class="flex h-full w-full items-center justify-center object-contain opacity-50 md:opacity-80"
              alt="The Ballad of a Native Man Poster"
            />
          </div>
          <div
            class="text-primary absolute inset-0 flex h-full flex-col items-center justify-center pt-[30px] text-[20px] md:static md:items-center md:justify-center md:pt-0"
          >
            <div
              class="text-style-primary font-style-2 mb-[10px] bg-black/80 text-center text-[30px] md:bg-transparent"
            >
              "The Ballad of a Native Man"
            </div>
            <div class="mb-[10px] bg-black/80 text-center md:bg-transparent">Short Film (2025)</div>
            <div class="bg-black/80 text-center md:bg-transparent">
              <span class="bg-black/80 pr-[5px] italic md:bg-transparent">Directed by:</span>
              Penny J. Gullion
            </div>
            <!--<div class="button2 pt-[30px]">
              <a href="https://www.imdb.com/title/tt34894135/" target="_blank">
                <img src="/assets/icons/IMDb.webp" class="h-[40px]" alt="IMDb Logo" />
              </a>
            </div>-->
            <div class="flex items-center justify-center pt-[30px] sm:pb-[70px]">
              <div class="w-[255px] lg:w-auto">
                <p class="p-2 text-xl font-semibold text-white">Score excerpts:</p>
                <div class="space-y-4">
                  <Audio
                    title="Uncertain Horizon"
                    src="/assets/audio/Ballad_excerpt000_master.wav"
                  />
                  <Audio title="Standoff" src="/assets/audio/Ballad_excerpt001_master.wav" />
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="mainminh-vr relative flex flex-col">
          <video
            autoplay
            muted
            loop
            playsinline
            class="absolute top-0 left-0 z-0 h-full w-full object-cover opacity-80"
          >
            <source src="/assets/videos/Vertical_Remains_Edit.mp4" type="video/mp4" />
          </video>
          <div class="relative z-10">
            <div class="text-primary flex flex-col pt-[100px] text-[20px]">
              <div
                class="text-style-primary font-style-2 mb-[10px] flex items-center justify-center text-[30px]"
              >
                "Vertical Remains"
              </div>
              <div class="mb-[10px] flex items-center justify-center">Short Film (2025)</div>
              <div class="flex items-center justify-center">
                <span class="pr-[5px] italic">Directed by:</span>
                Aadi Bhandari
              </div>
            </div>
            <div class="flex items-center justify-center pt-[30px] sm:pb-[70px]">
              <!---<div class="aspect-video w-full max-w-[1000px] px-4">
                <iframe
                  class="h-full w-full rounded-xl"
                  src="https://www.youtube.com/embed/lRgII2VKb38?si=Qlw34IM9JsidO6yQ"
                  frameborder="0"
                  allowfullscreen
                  title="youtuve video"
                  allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
                  loading="lazy"
                ></iframe>
              </div>-->
              <div class="w-[255px] lg:w-auto">
                <p class="p-2 text-xl font-semibold text-white">Score excerpts:</p>
                <div class="space-y-4">
                  <Audio title="Falling" src="/assets/audio/Verticality_excerpt1.wav" />
                  <Audio title="Descent" src="/assets/audio/Verticality_excerpt2.wav" />
                  <Audio title="Vertigo" src="/assets/audio/Verticality_excerpt3.wav" />
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="mainminh-poster relative md:grid md:grid-cols-2">
          <div class="mainminh-poster h-full">
            <img
              src="/assets/images/embed/Pulse.webp"
              class="flex h-full w-full items-center justify-center object-contain opacity-50 md:opacity-80"
              alt="Pulse Poster"
            />
          </div>
          <div
            class="text-primary absolute inset-0 flex h-full flex-col items-center justify-center pt-[30px] text-[20px] md:static md:items-center md:justify-center md:pt-0"
          >
            <div class="text-style-primary font-style-2 mb-[10px] text-[30px]">"Pulse"</div>
            <div class="mb-[10px] text-center">Short Film (2025)</div>
            <div class="text-center">
              <span class="pr-[5px] italic">Directed by:</span>
              Ben Mouland
            </div>
            <div class="button2 pt-[30px]">
              <a href="https://www.imdb.com/title/tt34894135/" target="_blank">
                <img src="/assets/icons/IMDb.webp" class="h-[40px]" alt="IMDb Logo" />
              </a>
            </div>
          </div>
        </div>

        <div class="mainminh-chrm relative flex flex-col">
          <video
            autoplay
            muted
            loop
            playsinline
            class="absolute top-0 left-0 z-0 h-full w-full object-cover opacity-80"
          >
            <source src="/assets/videos/002.mp4" type="video/mp4" />
          </video>

          <div class="relative z-10">
            <div class="flex flex-col pt-[100px] text-[20px]">
              <div
                class="text-style-primary font-style-2 mb-[10px] flex items-center justify-center text-[30px]"
              >
                "Chrome"
              </div>
              <div class="mb-[10px] flex items-center justify-center">Short Film (2024)</div>
              <div class="flex items-center justify-center">
                <span class="pr-[5px] italic">Directed by:</span>
                Joshua Brad-Lee Garrido
              </div>
            </div>
          </div>
          <div
            class="relative grid items-center justify-center pt-[30px] pr-[30px] pl-[30px] md:grid-cols-2"
          >
            <div>
              <iframe
                class="mb-6 max-w-[750px]"
                style="border-radius: 12px"
                src="https://open.spotify.com/embed/album/2jMIjOiD1fpCB0EMa72EaU?utm_source=generator&theme=0"
                width="100%"
                height="352"
                frameborder="0"
                title="spotiy album"
                allowfullscreen
                allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
                loading="lazy"
              ></iframe>
              <a
                class="button4 mb-12 flex max-w-[750px] items-center justify-center italic no-underline"
                href="../releases/chrome/"
                target="_blank"
              >
                OST OUT NOW
              </a>
            </div>
            <div class="grid grid-rows-2 items-center justify-center">
              <img
                src="/assets/laurels/chrome/laurels_cisa-officialselection_white.webp"
                class="max-h-[250px]"
                alt="Cannes Indie Shorts Official Selection Laurel"
              />
              <img
                src="/assets/laurels/chrome/NYUSFF_2025_Honorable_Laurel_white.webp"
                alt="NYU Sports Film Festival Honorable Mention Laurel"
                class="max-h-[200px]"
              />
            </div>
          </div>
        </div>

        <div class="mainminh-poster relative md:grid md:grid-cols-2">
          <div class="mainminh-poster h-full">
            <img
              src="/assets/images/embed/1s2.webp"
              class="flex h-full w-full items-center justify-center object-contain opacity-50 md:opacity-80"
              alt="One Swallow Two Poster"
            />
          </div>
          <div
            class="text-primary absolute inset-0 flex flex-col items-center justify-center pt-[30px] text-[20px] md:static md:items-center md:justify-center md:pt-0"
          >
            <div class="text-style-primary font-style-2 mb-[10px] text-center text-[30px]">
              "One Swallow Two"
            </div>
            <div class="mb-[10px] text-center">Short Film (2024)</div>
            <div class="text-center">
              <span class="pr-[5px] italic">Directed by:</span>
              Taryn Foster
            </div>
            <div class="button2 pt-[30px]">
              <a href="https://www.imdb.com/title/tt28080250/" target="_blank">
                <img src="/assets/icons/IMDb.webp" class="h-[40px]" alt="IMDb Logo" />
              </a>
            </div>
            <div class="flex items-center justify-center pt-[30px] sm:pb-[70px]">
              <div class="w-[255px] lg:w-auto">
                <p class="p-2 text-xl font-semibold text-white">Score excerpts:</p>
                <div class="space-y-4">
                  <Audio title="Demon Calling" src="/assets/audio/1s2_excerpt1_2_master.wav" />
                  <Audio title="Sweet Tragedy" src="/assets/audio/1s2_excerpt2_2_master.wav" />
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</div>
