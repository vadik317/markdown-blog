**A very simple blog website that uses markdown for your posts!  
All is powered by  `index.html`, where all the HTML, CSS, and JS does the job.**  

One day, I decided to create a blog, however, I couldn't find any easy to use repo, all of them had some fancy-pants framework or complex things like github actions and workflows, now, i'm going to assume that since you are reading this, i'm not the only one that can't for the life of me properly set up that, so I made a simpler solution:  
Having a single html file handle all the website, and a few simple config files in the very friendly `.json` format!  




Themes.json format:  
```
"id": "light",
    "name": "Light",
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
```


File structure:

```
your-blog/
├── index.html       (the main blog page I created)
├── blog-config.json (the configuration file for posts)
├── themes.json      (the configuration file for themes)
├── posts/
│   └── ... (your markdown posts)
└── images/
    └── ... (your post images)
```