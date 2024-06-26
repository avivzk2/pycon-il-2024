Website for PyCon Israel 2024
=============================

Website built with Pelican, using a PyCon-Israel-Flex theme
based on Flex.

Technicalities:
---------------

The Python side is managed by [Poetry](https://python-poetry.org/).
Use `poetry install` to get the dependencies.

The theme styling is built with gulp and other npm tools.
If you want to change anything in the CSS, 
- Preparation: Go to the folder `website_2024/themes/PyCon-Israel-Flex`,
  and there run the command `npm install`
- "Compilation" (mostly of the Less sources): Run the command
  `npm run build`
  
When you want to build the site itself, use `make html` from the
`website_2024` folder. It puts the built site in `output`. You
can use `make clean` to remove everything if you want to rebuild
from scratch; but it doesn't clean the theme files.

You can also use `make devserver` for the HTML, and `npm run watch`
for the styling -- these create watchers which update the output as
you change the source files.

Pages are in `website_2024/content/pages`, and are written in
Markdown. At the top of each page there is a block of metadata. Of
these, the `Title` field is very visible, but also critical are the
`Slug` and `Lang` fields which define the page identity (the Hebrew
and English versions of a page should have the same Slug; otherwise,
different pages should have different Slugs). The `page_number` field
determines the order of the page in the list of pages in the sidebar.

The home page content is defined like other pages, using files
`homepage.md` and `homepage-he.md` in `content/pages`; these contain
mostly HTML, since the homepage is not an "article" like other
pages. The metadata in these files has some unique fields, to choose
the different templates and to save the page as `index.html`.

The home page buttons and top is defined in the templates
`website_2024/themes/PyCon-Israel-Flex/templates/homepage.html` and
`.../homepage-he.html`. In the original template that came with the
Flex theme, this page lists articles (blog posts), but we don't want
that. The original template was kept for reference as
`index.html.orig`. 

Other interesting files to look at:
- The settings are defined in `website_2024/pelicanconf.py` (for
  development) and `publishconf.py` (for "production").
- The sidebar is defined in
  `website_2024/themes/PyCon-Israel-Flex/templates/partial/sidebar.html`
- The footer (currently still default, to be changed) is in 
  `website_2024/themes/PyCon-Israel-Flex/templates/partial/footer.html`
- All (non-partial) templates extend
  `website_2024/themes/PyCon-Israel-Flex/templates/base.html` -- that
  means that template defines structure for everything.


References of software used:
- Pelican: You can start at
  https://docs.getpelican.com/en/latest/content.html
- Flex, the base for the theme here:
  https://github.com/alexandrevicenzi/Flex
  + The intention is to have our theme serve many years, so we're
    keeping on the side a repo of the theme alone. You can mostly
    ignore it for now -- work inside the website repo; but that's why
    we try to keep things like the year in settings rather than the
    template source. The theme-only repo is
    https://github.com/Hamakor/PyCon-Israel-Flex
  + Also for future reference: https://github.com/AmirMahmood/Flex-RTL
    (it is based on an old version of Flex, though)
- The Pelican plugin for image processing (not yet in use):
  https://github.com/pelican-plugins/image-process
