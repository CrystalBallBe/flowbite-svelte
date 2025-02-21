<script lang="ts">
  import { quartInOut } from 'svelte/easing';
  import Toc from './Toc/+page.svelte';
  import '../app.css';
  import {
    DarkMode,
    Footer,
    FooterBrand,
    FooterCopyright,
    FooterIcon,
    FooterLink,
    FooterLinkGroup
  } from '$lib';
  import { Side, Nav, SidebarList } from 'svelte-sidebar-menu';
  import {
    forms,
    components,
    svelteflows,
    topMenus,
    typography,
    utilities,
    extend,
    experimental
  } from './moduleItems/+server.js';

  let asideClass =
    'absolute w-auto bg-white pt-8 shadow-lg z-40 h-screen px-4 overflow-scroll dark:bg-gray-900';

  // Nav
  let navDivClass = 'pb-4';
  // Navbar
  let logo = '/images/flowbite-svelte-icon-logo.svg';
  let logoClass = 'w-8 ml-0 sm:ml-4 sm:mr-2';
  let alt = 'Flowbite Svelte';
  let hamburgerClass =
    'text-gray-300 hover:text-blue-500 cursor-pointer mr-4 border-none focus:outline-none lg:hidden';
  let activeChildLi = 'block py-2 px-4 text-lg text-gray-700 hover:bg-gray-100 dark:text-white';
  let childLi =
    'block py-2 pr-4 pl-3 text-gray-700 border-b border-gray-100 md:border-0 md:p-0 text-base dark:text-white';
  let headerClass =
    'w-full z-50 px-6 bg-white h-14 pt-2 text-gray-600 border-b-2 dark:bg-gray-800 dark:text-white dark:border-b-1';
  let siteName = 'Flowbite Svelte';
  let navClass = 'py-0 px-4 text-base bg-white dark:bg-gray-900 dark:text-white';
  let siteClass = ' w-full pt-0.5';
  let spanClass =
    'pl-2 self-center text-md sm:text-lg font-semibold text-gray-900 whitespace-nowrap dark:text-white';

  let topli =
    'block py-2 pr-4 pl-3 text-gray-700 md:border-0 md:p-0 dark:text-gray-300  dark:hover:bg-gray-700 text-lg z-50  dark:bg-gray-800 dark:border-0 hover:bg-gray-100 bg-white';
  let topMenuDiv = 'flex flex-wrap justify-end items-center mx-auto dark:bg-gray-800 h-8 pr-8 pt-1 sm:pr-12';
  let topul =
    'flex flex-col mt-4 md:flex-row md:space-x-8 md:mt-0 md:text-md md:font-medium pt-1 dark:bg-gray-800 bg-white';

  let darkmodebtn =
    'text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 focus:outline-none focus:ring-4 focus:ring-gray-200 dark:focus:ring-gray-700 rounded-lg text-lg p-2.5 fixed right-4 top-2 z-50';
  let sideBarListClass = 'mb-4 px-0 xl:px-4 text-base';
  let h3Category = 'text-base pb-4 uppercase font-semibold';
  let transitionParams = {
    duration: 500,
    delay: 100,
    easing: quartInOut,
    x: -200
  };
</script>

<div class="px-4 mx-auto w-full max-w-full">
  <Side
    {siteName}
    {siteClass}
    {transitionParams}
    {topMenus}
    {headerClass}
    {asideClass}
    {logo}
    {logoClass}
    {alt}
    {activeChildLi}
    {spanClass}
    {topli}
    {topMenuDiv}
    {topul}
    {childLi}
    {hamburgerClass}>
    <Nav {navClass} class="pb-2">
      {#each svelteflows as { href, name, rel }}
        <SidebarList {href} {name} {sideBarListClass} />
      {/each}
    </Nav>
    <Nav {navClass} {navDivClass}>
      <h3 class={h3Category}>Components</h3>
      {#each components as { href, name, rel }}
        <SidebarList {href} {name} {sideBarListClass} />
      {/each}
    </Nav>
    <Nav {navClass} class="pb-2">
      <h3 class={h3Category}>Forms</h3>
      {#each forms as { href, name, rel }}
        <SidebarList {href} {name} {rel} {sideBarListClass} />
      {/each}
    </Nav>
    <Nav {navClass} class="pb-2">
      <h3 class={h3Category}>Typography</h3>
      {#each typography as { href, name, rel }}
        <SidebarList {href} {name} {rel} {sideBarListClass} />
      {/each}
    </Nav>
    <Nav {navClass} class="pb-2">
      <h3 class={h3Category}>Extend</h3>
      {#each extend as { href, name, rel }}
        <SidebarList {href} {name} {sideBarListClass} />
      {/each}
    </Nav>
    <Nav {navClass} class="pb-2">
      <h3 class={h3Category}>Utilities</h3>
      {#each utilities as { href, name, rel }}
        <SidebarList {href} {name} {rel} {sideBarListClass} />
      {/each}
    </Nav>
    <Nav {navClass} class="pb-24">
      <h3 class={h3Category}>Experimental</h3>
      {#each experimental as { href, name, rel }}
        <SidebarList {href} {name} {rel} {sideBarListClass} />
      {/each}
    </Nav>
  </Side>

  <main class="flex mx-auto pt-12 pb:12 xl:pb-24 lg:pb-16 lg:pl-60 ">
    <DarkMode btnClass={darkmodebtn} />
    <div class="w-full px-4 sm:px-8">
      <slot />
    </div>
    <div class="text-sm text-gray-500 dark:text-gray-400">
      <Toc />
    </div>
  </main>
</div>
<div class="mx-auto mb-4 pt-4 lg:pl-60">
  <Footer footerType="custom" customClass="py-6 px-16 bg-white dark:bg-gray-900">
    <div class="md:flex md:justify-between">
      <div class="mb-6 md:mb-0">
        <FooterBrand
          href="https://flowbite-svelte.com"
          src={logo}
          alt="Flowbite-Svelte Logo"
          name="Flowbite-Svelte" />
      </div>
      <div class="grid grid-cols-2 gap-8 sm:gap-6 sm:grid-cols-3">
        <div>
          <h2 class="mb-6 text-sm font-semibold text-gray-900 uppercase dark:text-white">Resources</h2>
          <FooterLinkGroup>
            <FooterLink liClass="mb-4" href="https://flowbite.com/">Flowbite</FooterLink>
            <FooterLink liClass="mb-4" href="https://tailwindcss.com/">Tailwind CSS</FooterLink>
          </FooterLinkGroup>
        </div>
        <div>
          <h2 class="mb-6 text-sm font-semibold uppercase text-gray-900 dark:text-white">Follow us</h2>
          <FooterLinkGroup>
            <FooterLink liClass="mb-4" href="https://github.com/themesberg/flowbite-svelte"
              >GitHub</FooterLink>
            <FooterLink liClass="mb-4" href="https://discord.gg/4eeurUVvTy">Discord</FooterLink>
          </FooterLinkGroup>
        </div>
        <div>
          <h2 class="mb-6 text-sm font-semibold uppercase text-gray-900 dark:text-white">Legal</h2>
          <FooterLinkGroup>
            <FooterLink liClass="mb-4" href="https://github.com/themesberg/flowbite-svelte/blob/main/LICENSE"
              >License</FooterLink>
          </FooterLinkGroup>
        </div>
      </div>
    </div>
    <hr class="my-6 border-gray-200 sm:mx-auto dark:border-gray-700 lg:my-8" />
    <div class="sm:flex sm:items-center sm:justify-between">
      <FooterCopyright href="/" by="Flowbite™" />
      <div class="flex mt-4 space-x-6 sm:justify-center sm:mt-0">
        <FooterIcon
          href="https://github.com/themesberg/flowbite-svelte"
          class="text-gray-400 hover:text-gray-900">
          <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true"
            ><path
              fill-rule="evenodd"
              d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
              clip-rule="evenodd" /></svg>
        </FooterIcon>
      </div>
    </div>
  </Footer>
</div>
