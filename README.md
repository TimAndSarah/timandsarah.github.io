
Tim And Sarah's Wedding Website
Uses Hugo framework. 


## Tutorials/Resources Used

- Forked from Sarah French's Github
https://github.com/SarahFrench/wedding-website
- [W3 Schools - How TO - Parallax Scrolling](https://www.w3schools.com/howto/howto_css_parallax.asp)
- [Animated Hamburger Menu Tutorial - CSS Effects](https://www.youtube.com/watch?v=dIyVTjJAkLw)


## Instructions:

 - Editing each section: 
   - Text and html are seperated:
      - Text is done inside the MD files inside /content and content/section.
      - HTML to do formatting/placing text on page is done inside the html files in layouts/partials
      - Leaf images are SVGs stored inside layouts/partials/svgs. SVGs have some templating information which Hugo can read, so they are different to static images.

 - Editing image files between sections:
      - Image files are stored in static/image.
      - They are defined as parameters inside /config.json
      - They are placed on the page inside layouts/partials/shared/dynamic_styles.html.
 
 - Page is built as follows:
    - layouts/_default/baseof.html is the template html. Inside here, there are Hugo "blocks" which are called. These blocks are:
      - dynamic_styles - the background images which go between sections of text
      - main - the sections of text
    - The Hugo "blocks" are defined inside layouts/index.html:
      - dynamic_styles - is built from the layouts/partials/shared/dynamic_styles.html file
      - main - built from the header.html, main.html, footer.html files inside layouts/partials/homepage and layouts/partials/shared
    - The webpage layout is basically all called inside the layouts/partials/homepage/main.html
      - Update this file if you need to add in text sections from layouts/partials/sections


## How to:

 - Add a text section:
    - Add a .md file (or edit existing) in content/section.
      - This file contains the plain text of the section.
    - Add a .html file (or edit existing) in layouts/partials/sections
      - Pull the .md file in using {{ $t := .Site.GetPage "/section/MD_FILE_NAME_HERE" }}
    - Update the layouts/partials/homepage/main.html file to pull in the new section
      - Use Hugo code: {{ partial "sections/HTML_FILE_NAME_HERE.html" . }} in the place you want it
  
  - Add an image to scroll past between sections: 
      - Ensure the image file you want is saved in the /static/image directory
      - Define the image in the params section of /config.json (such as "background_image_4": /image/IMG_FILE.JPG)
      - Define the image as a style in /layouts/partials/shared/dynamic_styles.html (such as .image4 { background-image: url("{{ .Site.Params.background_image_4 }}");} )
      - Update the /layouts/partials/homepage/main.html file to put a "div"" in the place you want the photo. Like this:  <div class="image image4"></div>
      
      
      
      
 

  
  


