<script>
  import MobileMenu from '../components/Home/MobileMenu.svelte'
  import IconList from '../components/IconList/IconList.svelte'
  export let templateHtml, settings
</script>

<style global lang="postcss">
  /* purgecss start ignore */
  @tailwind base;

  @tailwind components;
  /* purgecss end ignore */

  @tailwind utilities;

  /*

    @apply's

  */

  .myflexresponsive {
    @apply flex flex-col md:flex-row
  }
  .mylinkcolors {
    @apply dark:text-indigo-300 dark:hover:text-indigo-200 dark:focus:text-indigo-200 text-indigo-800
  }
  .mylink {
    @apply hover:underline focus:underline mylinkcolors
  }
  .mytext {
    @apply text-gray-800 dark:text-gray-200
  }
  .mytext-inverse {
    @apply text-gray-200 dark:text-gray-700
  }
  .mytext-light {
    @apply text-gray-600 dark:text-gray-300 mt-0
  }
  .bimodalblue {
    @apply text-blue-900 dark:text-blue-100 bg-blue-100 dark:bg-blue-900
  }
  .bimodalpurple {
    @apply text-purple-900 dark:text-purple-100 bg-purple-100 dark:bg-purple-900
  }

  /* replace typography plugin */
  .prose {
    @apply text-gray-700 dark:text-gray-300  leading-7
  }
  .prose {
    & p {
      @apply my-5
    }
    & li > p {
      @apply my-0 mt-3
    }
    & h1 {
      @apply text-black dark:text-white;
      font-weight: 800;
      font-size: 2.25em;
      margin-top: 0;
      margin-bottom: 0.8888889em;
      line-height: 1.1111111;
    }
    & h2, & h3, & h4, & h5, & h6 {
      @apply text-black dark:text-white;
      font-weight: 700;
      font-size: 1.5em;
      margin-top: 2em;
      margin-bottom: 1em;
      line-height: 1.3333333;
    }
    & strong {
      @apply text-gray-900 dark:text-gray-100 shadow-sm rounded
    }
    & a {
      @apply mylink
    }
    & pre {
      @apply text-xs p-6 bg-indigo-300 dark:bg-indigo-900 overflow-x-auto
    }
    & code {
      @apply text-sm bg-indigo-200 dark:bg-indigo-900 bg-opacity-50 px-1 py-2
    }
    & pre code {
      @apply bg-transparent p-0
    }
    & blockquote {
      @apply border-l-4 border-purple-800 dark:border-purple-200
    }
    & blockquote:before {
      @apply bg-purple-100 dark:bg-purple-900 bg-opacity-10
    }
    & ul {
      @apply leading-6 list-disc ml-4
    }
    & ul li {
      @apply mb-2 
    }
    & ul ul {
      @apply mt-2 
    }
    & img {
      @apply max-h-full my-4 mx-auto block
    }
  }


  /* 
  
  
  
  
  CUSTOM SCROLLBARS! https://css-tricks.com/the-current-state-of-styling-scrollbars/ 
  
  
  
  
  
  */
  body {
    --scrollbar-primary-color: #3730a3;
  }
  @media (prefers-color-scheme: dark) {
    body {
      --scrollbar-primary-color: #8db2e5;
    }
  }

  body::-webkit-scrollbar-track {
    background-color: var(--bg-color);
  }
  body::-webkit-scrollbar {
    width: 2vw;
  }
  body::-webkit-scrollbar-thumb {
    background: linear-gradient(var(--scrollbar-primary-color), var(--text-color));
    border-radius: 2px;
  }
  @media (min-width: 1000px) {
    body::-webkit-scrollbar-track {
      -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.9);
      background: radial-gradient(
        circle closest-side at 60% 43%,
        var(--bg-color) 26%,
        rgba(187, 0, 51, 0) 27%
      ),
      radial-gradient(
        circle closest-side at 40% 43%,
        var(--bg-color) 26%,
        rgba(187, 0, 51, 0) 27%
      ),
      radial-gradient(
        circle closest-side at 40% 22%,
        #e1e7ff 45%,
        rgba(221, 51, 85, 0) 46%
      ),
      radial-gradient(
        circle closest-side at 60% 22%,
        #e1e7ff 45%,
        rgba(221, 51, 85, 0) 46%
      ),
      radial-gradient(
        circle closest-side at 50% 35%,
        #e1e7ff 30%,
        rgba(221, 51, 85, 0) 31%
      ),
      radial-gradient(
          circle closest-side at 60% 43%,
          var(--bg-color) 26%,
          rgba(187, 0, 51, 0) 27%
        )
        50px 50px,
      radial-gradient(
          circle closest-side at 40% 43%,
          var(--bg-color) 26%,
          rgba(187, 0, 51, 0) 27%
        )
        50px 50px,
      radial-gradient(
          circle closest-side at 40% 22%,
          #e1e7ff 45%,
          rgba(221, 51, 85, 0) 46%
        )
        50px 50px,
      radial-gradient(
          circle closest-side at 60% 22%,
          #e1e7ff 45%,
          rgba(221, 51, 85, 0) 46%
        )
        50px 50px,
      radial-gradient(
          circle closest-side at 50% 35%,
          #e1e7ff 30%,
          rgba(221, 51, 85, 0) 31%
        )
        50px 50px;
      background-color: var(--bg-color);
      background-size: 20px 20px;
    }

    body::-webkit-scrollbar-thumb {
      -webkit-box-shadow: inset 0 0 10px rgb(0 0 0 / 90%), inset 0 0 0px 5px rgb(29 31 33 / 90%);
      border-radius: 10px;
      background-image: -webkit-linear-gradient(
        45deg,
        var(--scrollbar-primary-color) 25%,
        #fff 25%,
        #fff 50%,
        var(--scrollbar-primary-color) 50%,
        var(--scrollbar-primary-color) 75%,
        #fff 75%,
        #fff
      );
      background-size: 2rem 2rem;
    }
  }

  /* 
  
  
  
  CUSTOM PAGE BORDER - unused for now
  
  
  
  
  */
  /* body:before {
    content: '';
    position: fixed;
    max-width: 100vw;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: -1;
    border-radius: inherit;
    background: linear-gradient(#ff335f, #9198e5);
  } */
  /* background: linear-gradient(var(--brand-color-primary), #9198e5); */

  /* #base {
    transition: background-color 1s ease;
    background: var(--bg-color);
    min-height: calc(100vh - 10px);
    margin: 5px;
  }
  .basekid {
    min-height: calc(100vh - 10px);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  } */
</style>

<svelte:head>
  <link
    rel="stylesheet"
    href="{settings.locations.assets.replace('./public', '')}style.css" />
  <link rel="icon" type="image/png" href="/favicon.png" />
  <link rel="webmention" href="https://webmention.io/www.swyx.io/webmention" />
  <link rel="pingback" href="https://webmention.io/www.swyx.io/xmlrpc" />
  <meta name="theme-color" content="#818CF8">
  <script>
    if (
      'themePreference' in localStorage &&
      localStorage.themePreference === 'dark'
    ) {
      document.querySelector('html').classList.add('dark')
    } else if (
      !('themePreference' in localStorage) &&
      window.matchMedia('(prefers-color-scheme: dark)').matches
    ) {
      document.querySelector('html').classList.add('dark')
    }
  </script>
</svelte:head>
<div id="base">
  <div class="relative bg-gray-50 dark:bg-gray-900 overflow-hidden basekid">
    <MobileMenu hydrate-client={{}} />
    <!-- <main class="mt-8 sm:mt-16 md:mt-20 lg:mt-24"> -->
    <main>
      {@html templateHtml}
    </main>
    <!-- <footer class="pt-6 pb-12 sm:pb-32 text-white"> TODO: FOOTER</footer> -->
    <footer
      class="max-w-screen-xl mx-auto py-12 px-4 overflow-hidden sm:px-6 lg:px-8">
      <nav
        class="-mx-5 -my-2 myflexresponsive flex-wrap justify-center items-center px-5 py-2
          gap-2">
        <a
          href="/ideas"
          class="text-base leading-6 text-indigo-600 dark:text-indigo-400 hover:text-red-500">
          Ideas
        </a>
        <a
          href="/about"
          class="text-base leading-6 text-indigo-600 dark:text-indigo-400 hover:text-red-500">
          About
        </a>
        <!-- <a
          href="/subscribe"
          class="text-base leading-6 text-indigo-600 dark:text-indigo-400 hover:text-red-500">
          Subscribe
        </a> -->
      </nav>
      <div class="mt-8 flex justify-center">
        <IconList />
      </div>
      <div class="mt-8">
        <p class="text-center text-base leading-6 text-gray-400">
          &copy; 2017-2021 swyx. All rights reserved.
        </p>
      </div>
    </footer>
  </div>
</div>
