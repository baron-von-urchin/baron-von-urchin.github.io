# baronvonurchin

This website, baron-von-urchin.github.io, is my attempt to "re-claim" a domain name. I appreciate that GitHub lets you host two free domains at gitub.io (one for yourusername.github.io and one for youroganization.github.io). For a personal website that wasn't myusername.github.io I created an organization so that I could use Baron von Urchin in the url. 

After a lot of back and forth, and rage-quitting one to many times, I ended up with baron-von-urchin.github.io. Less than ideal, baronvonurchin.github.io _was_ mine, but after deleting that organization, the ur apparently became unavailable. Well, shit. 

Setting up a free organization was easy ([see: GitHub's documentation](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/creating-a-new-organization-from-scratch)), as ways [creating a Pages account](https://docs.github.com/en/pages/quickstart). I immediately ran into two big issues; knitting markdown documents to the project directory, and updating the "theme". 

For reasons I still don't understand, when I knit an MD script, it creates a folder called _site. Why? Dunno, can't figure it out. This was incredibly problematic because the .html outputs from my Rmd scipts were being housed in a subfolder of my working directory, so when I "built" the site, the YML had no idea where to go. So, none of my pages would load, or even techincally exists (404 error). I figured this all out when I copied the contents of the _site folder to the working directory. Oh well. 

The other issue I ran into related to the style via CSS scripts. To make a long story short, ignore the "choose a theme" section of the [Pages walkthroug](https://docs.github.com/en/pages/quickstart) walk through, and simply drop in a .css script into your project directory. For example, my problem was solved when I added the following script to the very bottom of _site.yml: 

```{r setup, include=FALSE}
output:
  html_document:
    # to avoid: [navbar-right flex css · Issue #316 · rstudio/flexdashboard](https://github.com/rstudio/flexdashboard/issues/316)
    #   get latest: devtools::install_github("rstudio/bslib")
    theme:
      # using bootstrap 4 with https://rstudio.github.io/bslib
      version: 5
      # see themes at https://bootswatch.com
      bootswatch: sandstone
    css: bootstrap.css
```
You specifically need the output to be "html_document" and the css to call a .css file that matches an expected outcome (e.g., I have a legacy styles.css script that still works, but bootstrap.css is what's currently called in version 5)

This brings me to the _site.yml script. I have no idea how you would set up tabular navigation in a normal GitHub pages account, but this script works nicely and is very use friendly. Simply create a _site.yml script like the one in your repo, and you're on your way to making an easily navigable site. Just make sure your .html script matches *exactly* what's in your _site.hyml script. The icons are from [Font Awesome](https://fontawesome.com/icons), these names *also* need to match perfectly. I simply created an Rmd script and knit to html (see issue #1 above). Once the .html script is saved properly in your wording directory, the _site.yml script will tell your user where to go, and how to get there. The bootswatch theme is applied to *all* pages on your site (so choose wisely). You can definitely customize pages within your chosen theme, but that's outside of my paygrade. 

Finally, I copied the "site_libs" folder and its contents from [FindingHal's repo](https://github.com/ecoquants/findinghal). Could just be a legacy, who knows. But the site works now, and that's all that matters. 

