<script lang="ts">
  import { page } from '$app/state';
  import { onMount } from 'svelte';
  import '../app.css';

  let { children } = $props();

  // State variables
  let menuOverlay: HTMLElement;
  let scrollToTop: HTMLElement;
  let mainHeader: HTMLElement;
  let bgHeader: HTMLElement;
  let lastScrollTop = 0;
  let lastScrollDownPos = 0;
  let isMenuOpen = $state(false);

  // Constants
  const scrollDownThreshold = 20;
  const scrollUpThreshold = 500;

  // Menu functions
  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }

  function closeMenu() {
    isMenuOpen = false;
  }

  function handleMenuClick(event: MouseEvent) {
    event.stopPropagation();
  }

  function handleDocumentClick() {
    closeMenu();
  }

  function handleMenuButtonClick(event: MouseEvent) {
    event.stopPropagation();
    toggleMenu();
  }

  function handleScrollToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  function handleScroll() {
    const currentScroll = window.scrollY;

    if (window.innerWidth < 768) {
      if (currentScroll === 0) {
        // Always show header at top of page
        mainHeader?.classList.remove('-translate-y-full');
        bgHeader?.classList.remove('-translate-y-full');
      } else if (currentScroll > lastScrollTop) {
        // Scrolling down
        if (currentScroll - lastScrollTop > scrollDownThreshold) {
          mainHeader?.classList.add('-translate-y-full');
          bgHeader?.classList.add('-translate-y-full');
          lastScrollDownPos = currentScroll;
        }
      } else if (currentScroll < lastScrollTop) {
        // Scrolling up
        if (lastScrollDownPos - currentScroll > scrollUpThreshold) {
          mainHeader?.classList.remove('-translate-y-full');
          bgHeader?.classList.remove('-translate-y-full');
        }
      }
    }

    lastScrollTop = currentScroll <= 0 ? 0 : currentScroll;
  }

  function handleResize() {
    if (window.innerWidth >= 768) {
      mainHeader?.classList.remove('-translate-y-full');
      bgHeader?.classList.remove('-translate-y-full');
    }
  }

  // Work visibility functions
  function hideWork() {
    const el = document.querySelector('.full-index-delay') as HTMLElement;
    if (el) {
      el.classList.add('hidden');
      setTimeout(() => {
        el.style.zIndex = '0';
      }, 500);
    }
  }

  function showWork() {
    const el = document.querySelector('.full-index-delay') as HTMLElement;
    if (el) {
      el.style.zIndex = '999';
      requestAnimationFrame(() => {
        el.classList.remove('hidden');
      });
    }
  }

  // Form handling
  function handleFormInputs() {
    const form = document.querySelector('form');
    if (!form) return;

    const inputs = form.querySelectorAll('input, textarea') as NodeListOf<
      HTMLInputElement | HTMLTextAreaElement
    >;

    inputs.forEach((input) => {
      const saved = localStorage.getItem(input.name);
      if (saved) input.value = saved;

      input.addEventListener('input', () => {
        localStorage.setItem(input.name, input.value);
      });
    });
  }

  onMount(() => {
    // Add event listeners
    window.addEventListener('scroll', handleScroll);
    window.addEventListener('resize', handleResize);
    document.addEventListener('click', handleDocumentClick);

    // Handle form inputs
    handleFormInputs();

    // Cleanup function
    return () => {
      window.removeEventListener('scroll', handleScroll);
      window.removeEventListener('resize', handleResize);
      document.removeEventListener('click', handleDocumentClick);
    };
  });

  // Make functions globally available if needed
  if (typeof window !== 'undefined') {
    (window as any).hideWork = hideWork;
    (window as any).showWork = showWork;
  }

  const getBgClass = () => {
    switch (page.url.pathname) {
      case '/':
        return "fade-in-page bg-[url('/assets/images/backgrounds/background.jpg')] bg-contain";
      case '/about/':
        return "bg-[url('/assets/images/backgrounds/background_50.png')]";
      case '/news/':
        return "bg-[url('/assets/images/backgrounds/background_50.png')] md:bg-[url('/assets/images/backgrounds/backgroundXflip_25.png')]";
      case '/work/':
        return "bg-[url('/assets/images/backgrounds/background_50.png')] md:bg-[url('/assets/images/backgrounds/backgroundXflip_10.png')]";
      case '/contact/':
        return "bg-[url('/assets/images/backgrounds/backgroundXflip_50.png')]";
      default:
        if (page.url.pathname.startsWith('/releases/')) {
          return "bg-[url('/assets/images/backgrounds/background_50.png')] md:bg-[url('/assets/images/backgrounds/backgroundXflip_25.png')]";
        }
        return "bg-[url('/assets/images/backgrounds/background_50.png')]";
    }
  };
</script>

<svelte:head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
  <link
    href="https://fonts.googleapis.com/css2?family=Wittgenstein:ital,wght@0,400..900;1,400..900&display=swap"
    rel="stylesheet"
  />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
  <link
    href="https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100..900;1,100..900&display=swap"
    rel="stylesheet"
  />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
  <link
    href="https://fonts.googleapis.com/css2?family=Roboto+Condensed:ital,wght@0,100..900;1,100..900&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<div class={`flex min-h-screen flex-col bg-black bg-fixed bg-no-repeat ${getBgClass()}`}>
  <header
    bind:this={bgHeader}
    id="bgHeader"
    class="mask-to-t full-hidden-headerbg full-index-headerbg fixed flex h-[240px] w-full bg-black transition-transform duration-300 ease-in-out sm:h-[180px]"
  ></header>

  <header
    bind:this={mainHeader}
    id="mainHeader"
    class="font-style-2 full-header-width fixed z-100 flex h-[180px] w-full justify-between pt-[20px] pb-[20px] transition-transform duration-300 ease-in-out sm:h-[128px]"
  >
    <div
      bind:this={scrollToTop}
      id="scrollToTop"
      class="flex h-full flex-col items-start justify-center pl-[30px] transition-opacity duration-300 ease-in-out md:opacity-100"
      role="button"
      tabindex="0"
      onclick={handleScrollToTop}
      onkeydown={(e) => e.key === 'Enter' && handleScrollToTop()}
    >
      <a href={page.url.pathname === '/' ? '/' : '/about'}>
        <h1 class="pb-[5px] text-[35px] font-[700] tracking-widest text-nowrap">
          MUNGO
          <span class="inline sm:hidden"><br /></span>
          MCLAGGAN
        </h1>
      </a>
      <h2 class="text-secondary mt-[-8px] mb-[8px] text-[20px] sm:mt-[-12px]">COMPOSER</h2>
      <div class="button-group flex space-x-3 opacity-80">
        <div class="button">
          <a href="https://www.instagram.com/mungomclaggan/" target="_blank">
            <img src="/assets/icons/Instagram_white.png" class="h-[30px]" alt="Instagram" />
          </a>
        </div>
        <div class="button">
          <a href="https://www.youtube.com/@mungomclaggan" target="_blank">
            <img src="/assets/icons/Youtube.png" class="h-[30px]" alt="YouTube" />
          </a>
        </div>
        <div class="button">
          <a href="https://open.spotify.com/artist/27ZwIPgJ1SX3iIjvHyyH07" target="_blank">
            <img src="/assets/icons/Spotify_white.png" class="h-[30px]" alt="Spotify" />
          </a>
        </div>
        <div class="button">
          <a href="https://music.apple.com/artist/mungo-mclaggan/1611932686" target="_blank">
            <img src="/assets/icons/AppleMusic_white.png" class="h-[30px]" alt="Apple Music" />
          </a>
        </div>
        <div class="button">
          <a href="https://www.imdb.com/name/nm16731844/" target="_blank">
            <img src="/assets/icons/IMDb.png" class="h-[30px]" alt="IMDb" />
          </a>
        </div>
      </div>
    </div>

    {#if page.url.pathname !== '/'}
      <menu class="relative flex w-full items-end justify-end pr-[20px] text-[30px] md:hidden">
        <button
          id="menuButton"
          class="text-button z-50 focus:outline-none"
          onclick={handleMenuButtonClick}
        >
          Menu
        </button>
      </menu>
    {/if}

    <!-- svelte-ignore a11y_click_events_have_key_events -->
    <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
    <ul
      bind:this={menuOverlay}
      id="menuOverlay"
      class="mask-to-t2 absolute top-0 right-[130px] left-0 z-40 flex h-[180px] w-full flex-col justify-center gap-y-[15px] bg-black pl-[10px] transition-opacity duration-300 sm:h-[128px] sm:justify-start sm:gap-y-[0px] sm:pt-[25px] md:hidden"
      class:opacity-0={!isMenuOpen}
      class:pointer-events-none={!isMenuOpen}
      onclick={handleMenuClick}
    >
      <li
        class="mt-[50px] mb-[37px] flex items-center justify-between pr-[4vw] pl-[20px] text-[25px] sm:mt-[0px] sm:mb-[0px] sm:pr-[6vw] sm:pb-[28px]"
      >
        <a href="/about/" class={`text-button ${page.url.pathname === '/about/' ? 'selected' : ''}`}>
          About
        </a>
        <span class="mx-2 h-[30px] w-[2px] bg-white/30"></span>
        <a href="/work/" class={`text-button ${page.url.pathname === '/work/' ? 'selected' : ''}`}>
          Work
        </a>
        <span class="mx-2 h-[30px] w-[2px] bg-white/30"></span>
        <a href="/news/" class={`text-button ${page.url.pathname === '/news/' ? 'selected' : ''}`}>
          News
        </a>
        <span class="mx-2 h-[30px] w-[2px] bg-white/30"></span>
        <a
          href="/contact/"
          class={`text-button ${page.url.pathname === '/contact/' ? 'selected' : ''}`}
        >
          Contact
        </a>
      </li>
      <li
        class="button-group ml-[20px] flex w-[195px] items-end justify-start space-x-3 opacity-80"
      >
        <div class="button">
          <a href="https://www.instagram.com/mungomclaggan/" target="_blank">
            <img src="/assets/icons/Instagram_white.png" class="h-[30px]" alt="Instagram" />
          </a>
        </div>
        <div class="button">
          <a href="https://www.youtube.com/@mungomclaggan" target="_blank">
            <img src="/assets/icons/Youtube.png" class="h-[30px]" alt="YouTube" />
          </a>
        </div>
        <div class="button">
          <a href="https://open.spotify.com/artist/27ZwIPgJ1SX3iIjvHyyH07" target="_blank">
            <img src="/assets/icons/Spotify_white.png" class="h-[30px]" alt="Spotify" />
          </a>
        </div>
        <div class="button">
          <a
            aria-label="apple music artist"
            href="https://music.apple.com/artist/mungo-mclaggan/1611932686"
            target="_blank"
          >
            <img alt="apple music icon" src="/assets/icons/AppleMusic_white.png" class="h-[30px]" />
          </a>
        </div>
        <div class="button">
          <a href="https://www.imdb.com/name/nm16731844/" target="_blank">
            <img src="/assets/icons/IMDb.png" class="h-[30px]" alt="IMDb" />
          </a>
        </div>
      </li>
    </ul>
  </header>

  {#if page.url.pathname !== '/'}
    <nav
      class="font-style-2 invisible fixed z-1000 mt-[180px] h-full w-[250px] pl-[20px] md:visible md:w-[150px]"
    >
      <ul class="grid grid-cols-1 space-y-9 text-[20px] font-bold tracking-widest">
        <li class="flex justify-end">
          <a
            href="/about/"
            class={`text-button ${page.url.pathname === '/about/' ? 'selected' : ''}`}
          >
            About
          </a>
        </li>
        <li class="flex justify-end">
          <a href="/work/" class={`text-button ${page.url.pathname === '/work/' ? 'selected' : ''}`}>
            Work
          </a>
        </li>
        <li class="flex justify-end">
          <a href="/news/" class={`text-button ${page.url.pathname === '/news/' ? 'selected' : ''}`}>
            News
          </a>
        </li>
        <li class="flex justify-end">
          <a
            href="/contact/"
            class={`text-button ${page.url.pathname === '/contact/' ? 'selected' : ''}`}
          >
            Contact
          </a>
        </li>
      </ul>
    </nav>
  {/if}

  {@render children()}
  <footer
    class={`flex min-h-[80px] w-full flex-grow flex-col items-center justify-center space-y-2 opacity-65 ${page.url.pathname !== '/' ? 'md:pl-[150px]' : ''}`}
  >
    <div class="inline justify-start text-center text-3xl">
      <h1 class="text-secondary text-[15px]">Copyright © 2025 Mungo McLaggan</h1>
    </div>
  </footer>
</div>
