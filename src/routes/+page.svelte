<!-- +page.svelte -->
<script>
       import { page } from "$app/stores";
       import {
              Header,
              Hero,
              Section,
              Main,
              Blockquote,
              Footer,
              Theme,
              Divider
       } from "@onsvisual/svelte-components";

       const customStylesheet = $page.url.searchParams.get("customStylesheet");

</script>

{#if customStylesheet}
       <link rel="stylesheet" href={customStylesheet} />
{/if}

<Header compact />
<Main>
       <Hero
              title="This is an article title"
              lede="This is a short, introductory sentence"
              date="2023-07-04"
       >
              <!-- <Checkbox label="Enable animation" variant="ghost" checked={animation} noBorder/> -->
       </Hero>

       <Theme theme="light">
              <Section title="Section title in light theme" marginTop={true}>
                     <p>Some dummy text</p>
                     <Blockquote attribution="A. Person">
                            This is a blockquote, white comprises of a large
                            block of inset text.
                     </Blockquote>
                     <p>
                            Lorem ipsum dolor sit amet, consectetur adipiscing
                            elit, sed do eiusmod tempor incididunt ut labore et
                            dolore magna aliqua. Ut enim ad minim veniam, quis
                            nostrud exercitation ullamco laboris nisi ut aliquip
                            ex ea commodo consequat. Duis aute irure dolor in
                            reprehenderit in voluptate velit esse cillum dolore
                            eu fugiat nulla pariatur. Excepteur sint occaecat
                            cupidatat non proident, sunt in culpa qui officia
                            deserunt mollit anim id est laborum.
                     </p>
              </Section>
              <Theme theme="dark">
                     <Section title="Section in dark theme " marginTop={true}>
                            <p>
                                   This section is actually nested in the light
                                   theme.
                            </p>
                     </Section>
                     <Divider />
              </Theme>
       </Theme>

       <Theme theme="lightblue">
              <Section title="Section in light blue" marginTop={true}>
                     <p>This section is in the light blue theme.</p>
              </Section>
       </Theme>
       <Theme theme="light" allowClientOverrides={true}>
              <Section title="Section with client overrides" marginTop={true}>
                     <p>This section has custom colours and custom fonts e.g. here we are using the BBC Reith Serif.</p>
              </Section>
       </Theme>
</Main>
<Footer compact />


