<script>
  import Audio from '../../components/Audio.svelte';
</script>

<section class="flex flex-col">
  <div class="mainminh full-padding flex flex-grow flex-col pt-[200px] sm:pt-[132px] md:ml-[150px]">
    <div
      class="text-secondary custom-bg-opacity mask-to-t2 mx-auto flex w-full max-w-[1000px] flex-col space-y-8 overflow-y-auto bg-[rgba(0,0,0,var(--bg-opacity))] p-6 leading-relaxed transition-colors duration-500 [word-spacing:0.1rem] sm:p-12"
    >
      <div class="flex flex-col pt-[20px] md:grid md:grid-cols-2">
        <!--Remeber to take off the pt-[30px] if adding a new item on top-->
        <img alt="Mungo" src="/assets/images/embed/mungo_5.1.5.png" />
        <p
          class="text-style-primary font-style-2 self-end pt-3 text-[clamp(1.5rem,4vw,3rem)] md:pt-0 md:pl-6 md:text-[clamp(1.5rem,3vw,2rem)]"
        >
          Mungo McLaggan is a British-Canadian
          <span class="text-style-primary">film composer</span>
          based in Vancouver, Canada.
        </p>
      </div>
      <div class="mt-[-15px] mb-[60px] flex flex-col space-y-[24px] md:mt-0">
        <p>
          Growing up in the UK, Mungo's journey into musical composition arguably started at age 5
          when he began studying piano. Throughout his school days, he sang in various choirs
          amassing almost a decade of choral singing experience. His musical practices have led him
          to perform in many renowned venues across England including
          <span class="text-style-primary">Smith Square Hall, London,</span>
          and
          <span class="text-style-primary">Queen's College, Oxford.</span>
        </p>
        <p>
          As a natural born performer, Mungo got his first taste of the film industry in front of
          the camera as a child actor. Later, as a graduate of the
          <a class="button4" target="_blank" href="https://www.ubc.ca/">
            University of British Columbia's
          </a>
          highly selective
          <span class="text-style-primary">Film Production</span>
          program, he gained a deep understanding of all aspects of film and media production, putting
          him in a uniquely versatile position as a composer.
        </p>
        <p>
          Mungo's work thus seeks to explore new ways in which music and visual media can coalesce
          to serve a higher narrative and emotional function.
        </p>
        <p>
          Recent work includes scores for a number of short films spanning a diverse range of
          genres. Music, including his recent
          <a class="button4" href="../news/#chrome">award-winning</a>
          score for the short film
          <span class="text-style-primary italic">Chrome,</span>
          can be found on
          <a class="button4" href="../releases/chrome/" target="_blank">
            all major streaming services.
          </a>
        </p>
      </div>
      <span class="h-[2px] w-full bg-white/30"></span>

      <div class="font-style-2 mt-[60px] flex flex-col space-y-[100px]">
        <div class="pr-[24px] pl-[24px]">
          <h1 class="text-style-primary mb-[24px] text-center text-[30px] md:mb-[50px]">
            LATEST RELEASE:
          </h1>
          <div class="flex flex-col md:grid md:grid-cols-2">
            <a href="../releases/chrome/" target="_blank">
              <img
                class="button3"
                src="/assets/images/embed/(FINAL)_Soundtrack_Album_Art_006_7.1.5.jpg"
              />
            </a>
            <h1
              class="text-style-primary mt-[24px] flex flex-col items-center justify-center text-center text-[30px] md:mt-0 md:ml-[24px]"
            >
              Chrome (Original Motion Picture Soundtrack)
              <span class="text-secondary text-center text-[25px]">September 28th, 2024</span>
            </h1>
          </div>
        </div>

        <span class="h-[2px] w-full bg-white/30"></span>

        <div class="font-style-2 pr-[24px] pl-[24px] xl:mb-[124px]">
          <h1 class="text-style-primary font-style-2 mb-[20px] text-center text-[30px]">
            RECENT NEWS:
          </h1>
          <div class="flex flex-col">
            <h1 class="text-style-primary mb-[30px] text-[30px]">
              <span class="flex items-center justify-start">
                One Swallow Two premieres at Whistler Film Festival!
              </span>
              <span class="text-secondary flex items-center justify-start text-[25px]">
                December 5th, 2024
              </span>
            </h1>
            <a href="../news/" target="_blank">
              <img class="button3" src="/assets/images/embed/1s2.png" />
            </a>
          </div>
          <h1 class="text-secondary mt-[36px] text-center font-[Wittgenstein] text-[20px]">
            (more on the
            <a href="../news/" class="button4 font-light">news</a>
            page)
          </h1>
        </div>
      </div>
    </div>
  </div>
</section>
