# Notes about page structure on page-about.hbs

Remember that **flex** is a shorthand for flex grow, flex shrink, and flex basis. The idea is that, for example, main.o-wrapper with **flex: 1 0 auto** will grow to 1, relative to other flexible items in the flex container. It will also shrink to 0 relative to those other items. Flex basis is the starting size of the item. 

In the case of main.o-wrapper, it has two siblings (header and footer) within a flex container (div.c-site-container). Header and footer just have the default flex value of **flex: 0 1 auto**. The flex direction is set to column. The container's min height is 100vh - that's the full view screen. 

## Structure

- body.page-template {no styles here}
    - div.c-site-container {display: flex; min-height: 100vh; flex-direction: column;}
        - header.c-header {padding and color styles}
        - main.o-wrapper {flex: 1 0 auto}
          - div.o-grid {display:flex;flex-wrap:wrap;max-width:1200;margin:0 auto;}
            - div.o-grid__col {flex-grow:1 and some padding}
            - - o-grid__col--center {flex-grow:initial;margin:0 auto;}
            - - o-grid__col--9-10-m {width:90%} - @min-width:40em
            - - o-grid__col--2-3-l {width:66%} - @min-width:64em
            - - o-grid__col--4-4-l {width:100%} - @min-width:64em
              - div.c-home {display: grid;grid-template-columns: repeat(2,1fr);grid-template-rows: 1fr;grid-column-gap: 40px;grid-template-areas: "media content";}
                - div.c-home__media {grid-area:media}
                - div.c-home__content {grid-area:content}
          - div.o-grid
          - div.o-grid
          - div.o-grid
          - div.o-grid
          - div.o-grid
          - div.o-grid
        - footer.c-footer {}

o-grid is display: flex and flex-wrap: wrap on screens over 40em wide.

# Search Idea

Stork is a modern, currently maintained search package. Stork can index a set of content. The index is then made available to Stork on your site. As you type, stork returns results from the index.

For this to work, you'd need to use Github Actions or Netlifly functions or something similar to create a script to regularly re-index all of the content on georgepillsbury.com. And that script would have to trigger anytime the site's content is altered. 

Very hard.

1. Using Github Actions or similar
2. Using Ghost content API
3. Generating content file from Ghost content API
4. Using stork to index content file