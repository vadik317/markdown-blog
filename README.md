**A very simple blog website that uses markdown for your posts!  
All is powered by _a single html file (scaryyy)_, where all the HTML, CSS, and JS does the job.**  

One day, I decided to create a blog, however, I couldn't find any easy to use repo, all of them had some fancy-pants framework or complex things like github actions and workflows, now, i'm going to assume that since you are reading this, i'm not the only one that can't for the life of me properly set up that, so I made a simpler solution:  

Having a single html file handle all the website, and a few simple config files in the very friendly `.json` format!  
You can check it out [here](https://vadik317.github.io/markdown-blog/).

There are some things I still need to do before this can be considered finalized:
* Fix the indentation in the html
* Extend the themes function to all css, so any color can be cohanged from config
* Explain properly everything in documentation
* Properly integrade the markdown parser to be nearly identical to github's parser
* Add the functionality for entry cards to have images
* Make the site more friendly towards mobile devices

</br>

If you find any bugs, please submit an issue, and if you can help me out and contribute, make a pr, ill be very glad to receive some help!  

![Damn the image didn't load, it was supposed to be a cat in front of a laptop](/images/cat-sitting-on-laptop.webp)
---

This project is intended to be able to run on any http server, so yes, you can test locally using `$ python -m http.server`, this also means that to set this up using github pages, you only need to enable them in your repo, as long as `index.html` exists, everything will be done automatically.  
Down below I have a simple guide on how to user this project.

---
Now, you may want to use this for yourself, and thats great! Here i'll provide a simple documentation on how everythign works.  
To start, simply download this repo, and remove all my blogs from `/posts`, and also remove the references from `blogs.json`  
Something I ommited earlier is that we use a separate `blogs.json` file to index our blogs, since doing api calls to github and checking every single file is not a great idea (and totally not because I dont know how to do it). This means every time you create a blog entry, you have to reference it here.

Before we go further lets just look at the folder structure:
```
your-blog/
├── index.html   (the main blog page)
├── blogs.json   (the configuration file for posts)
├── themes.json  (configuration for themes)
├── fonts.json   (configuration for fonts)
├── config.json  (configuration for the website)
├── posts/
│   ├── blog-1.md (your markdown posts)
│   └── ...       
└── images/
    ├── image.webp (your post images)
    └── ... 
```
You should follow this simple structure as thats how the website works, also I recommed using `webp` since its a light format, but markdown supports `jpg` and `png` among others.  

**BEFORE WE CONTINUE, PLEASE NOTE THAT JSON DOESN'T SUPORT COMMENTS, SO PLEASE REMOVE THEM IF YOU COPY THE EXAMPLES BELOW**  
`//hi im a comment please don't put me in .json files `

Next, this is how you configure your site in `config.json`:
```
{
  "blogTitle": "Vadik317's Markdown Blog", //The main title at the top of the site
  "githubUrl": "https://github.com/vadik317/markdown-blog", //Link to this repo (you can change it :D)
  "postsPerPage": 8, //How many posts to display per page
  "defaultTheme": "light", //The id of the default theme to use
  "defaultFont": "sans-serif" //The id of the default font to use
}
```  

This is how you index one of your blogs, using the `blogs.json` file:
```
{
  "posts": [
    {
      "title": "Why I love markdown",  //title of your post
      "description": "I really like markdown and you should check it out!", //small description only visible on entry card
      "file": "posts/why-markdown-is-cool.md", //link to the file, telling the site where it is located
      "date": "11-07-2025", //the date when you publish this
      "tags": ["programming","featured"], //tags to make it easier to find
      "image": "images/image.webp" //currently doesn't work <sad face>
    }
  ]
}
```

Next, this is how to make a custom theme using the `themes.json` file:  
(if you want to add some to the main branch I dont mind, submit a pr)  
```
[{
"id": "light",   //id of the theme
"name": "Light", //the displayed name of the theme
"colors": {
"bgPrimary": "#ffffff",     //background color of website
"textPrimary": "#222222",   //text color
"containerBg": "#ffffff",   //backround of the blog window
"sidebarBg": "#f5f5f5",     //backround of sidebar
"borderColor": "#e0e0e0",   //no use right now
"accentColor": "#666666",   //controls scrollbar color
"tagBg": "#888888",         //backround of tags
"navStart": "#888888",      //left of top bar (gradient)
"navEnd": "#666666",        //right of top bar
"postItemBg": "#f5f5f5",    //backround of each post entry
"postItemHover": "#e8e8e8", //backround of each post entry on hover
"codeBg": "#eeeeeeff"}      //backround of code in markdown  
}]
```

Finally, this is how you add more font options using the `fonts.json` file:
```
[
  {
    "id": "sans-serif", //id of the font
    "name": "Sans Serif", //displayed name for the font
    "value": "'Segoe UI', Roboto, Helvetica, Arial, sans-serif" //fonts to represent this selection
  }
]
```
Note that you can include several fonts in one, this is because we want to have fallback fonts if one cannot render, in this case, we would first try _Segoe UI_, then _Roboto_, etc...  
Another thing to note is that for now, if you wish to add custom fonts, you need to reference them in `index.html`, for example:
```
...
<script src="https://cdn.jsdelivr.net/gh/highlightjs/cdn-release@11.7.0/build/highlight.min.js"></script>
<!-- ubuntu mono font -->
<link href="https://fonts.googleapis.com/css2?family=Ubuntu+Mono:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
<style>
...
```
