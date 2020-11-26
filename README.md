
![enter image description here](https://miro.medium.com/max/875/1*A_Pdvofzw4jGyh50BvzK2A.jpeg)
# Building a portfolio website with VueJs
Building a portfolio website from scratch is a great method to learn web development. It helps developers to show their creativity and improve their problem-solving capability. These were the two keystones that I wanted to improve upon. I picked VueJs a few months back and wanted to explore further into this framework.
[For live preview click here.](https://ayushman.me/)
## What is Vuejs?
![enter image description here](https://miro.medium.com/max/875/1*MStmxLf35FfrH6Lpp2PEpg.png)
The three main front-end frameworks that are currently dominating the market are React, Angular and Vue, with React being the most popular and Vue being the easiest. These frameworks helps in building user interfaces and single-page applications. The reason why I picked VueJs over other frameworks was its easy to go through documentation and its clean syntax.
## Research and Searching for Ideas
From the start, I was aware about the possibility of creating UI too artistic and throwing User Experience out of the window. I had seen websites that made jaw drop from the aesthetics but I never understood where I was suppose to click and what was the flow. So I read few articles about portfolio websites and typography and created bullet points for myself to follow.

 - Have a proper Call To Action (CTA). 
 - Don’t make the user feel lost.
 - Make user click less.
 I wanted my design to follow these points.
 
![enter image description here](https://miro.medium.com/max/625/1*vAm0GYAW-pP5XOoYTniYlg.png)


I did what I always do before designing any UI. I went to dribbble and behance for inspiration and searched for portfolio websites. There were so many designs, but the one I liked the most was by [Alex Sanmartino](https://www.behance.net/gallery/97854185/Alex-Sanmartino-Personal-Branding?tracking_source=search_projects_recommended%7Calex%20sanmartino).
## Wireframing & Designing
I drew rough sketches for each section. In my design, a single section takes a minimum of 100% viewport height (vh) and viewport width (vw)[These are CSS units. Basically its means each section will cover everything from top left to bottom right of the visible browser’s view].

**Home Section**

![enter image description here](https://miro.medium.com/max/875/1*6_jAKhRBGFtzJhbLbJ4gPQ.png)

For Home section, I kept the design minimal. There’s my name, image and a big CTA button. On the top right, there’s a hamburger menu for easy navigation and on top left, there my logo.

**About Me Section**

![enter image description here](https://miro.medium.com/max/875/1*kEGPq-Bpog1nBLJIJhfalQ.png)

In the second section, I gave a brief description about myself. Below description there’s few logos of the technologies that I’m good with. It also helps viewer with a quick overlook of my skills.

**Work Section**

![enter image description here](https://miro.medium.com/max/875/1*tsrkPrMPuPhLGRxFCa8mgA.png)

Each box contains details about a single project. These boxes contains a title, a tag to describe type of project, preview buttons on top right, description, cover image and a read more button. I also gave a filter option at the top for users to quickly list similar types of projects.

**Find Me Section**

![enter image description here](https://miro.medium.com/max/875/1*0BQSVQtln1XZdoXuJmJRnw.png)

In the last section, there’s a grid of different platforms where viewer can go and explore more about me.
## Putting the pieces together
After finalizing the design of the portfolio, the next step was to look into the programming aspect of it. I won’t go into much technical detail, but I’ll try to give an overview of the logics and project structure.

Let’s start by diving a little deeper into Vuejs.

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta http-equiv="X-UA-Compatible" content="IE=edge" />
<meta name="viewport" content="width=device-width,initial-scale=1.0" />
<link rel="icon" href="<%= BASE_URL %>favicon.ico" />
<title><%= htmlWebpackPlugin.options.title %></title>
</head>
<body>
<noscript>
<strong
>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work
properly without JavaScript enabled. Please enable it to
continue.</strong>
</noscript>
<div id="app"></div>
<!-- built files will be auto injected -->
</body>
```

The way vuejs works is injects itself to a div inside an html file and everything inside that div is rendered by vuejs engine.

In the above code snippet, the html file is mostly empty besides a div with id of app.
In vuejs we have components which are reusable Vue instances. These components are building blocks of a website.

### Lets take an example of medium’s sidebar.

![enter image description here](https://miro.medium.com/max/619/1*vQUWcdPMBb9FKFy3XfaIhg.png)

Here we have two different blocks, one showing **Latest From Following** which have icons with name and notifications and other being **Topics You Follow** which only has topic’s name that I follow. If we want to recreate this in vuejs. We will have two components, one for each section. The first component will get values such as name, image and notification number as props[props are values that parent component sends to its child component] and then we will use those values to render a single profile. The second component can be for **Topics You Follow** which takes in name and return a single tag. Then we can reuse the same components with different values and it will give us a list of profiles and a list of tags.

When you create a vue project with **`vue create <project-name>`**. It creates most of the boilerplate files. But I added few tweaks in the structure of the project.

![Project structure](https://miro.medium.com/max/438/1*L4tdsqmGr5_S2nhi4P6kFw.png)


This is how I organized my project. The assets folder have icons, images, pattern and data for my work projects. This **projectData.js** file is exporting an array of objects where I’m storing details for my every project.

```
export default [
  {
    mitio: {
      category: "Programming",
      content:
        "Mitio is a weather app that I created to have a better understanding of the web development process and what it takes to build a web app. I wanted to create a simple-looking weather app without using any third-party libraries (except for animation). I tried to keep the design simple and practical where user can have access to the weather information without much hassle.",
      preview_links: {
        github: "https://github.com/ayushman-git/weather-app",
        behance: "https://www.behance.net/gallery/105557995/Mitio",
        live: "https://weathertestapp.netlify.app/",
      },
      image: "https://i.imgur.com/yGycZYW.jpg",
      article:
        "https://medium.com/@Duoro/mitio-weather-simplified-ae8bce8626db",
      favorite: "Favorites",
    },
  },
  ...
```
In my components folder, I have components that I’m using throughout my project. I’ll go through each component later.

In my section folder, I am dealing with individual parts of the page. For eg. **Home.vue** is responsible for the first section. So if we divide the whole structure of my project into tree, it would look like this.

![enter image description here](https://miro.medium.com/max/1250/1*Y7sJHm4wRy6_xlHA_KyIlw.png)


## Components
**Home.vue > Hero.vue**

![enter image description here](https://miro.medium.com/max/875/1*gKPkfHI3Fd7ocLruljVwog.png)

Its a flexbox containing two elements. One is a div which contains text on the left side and an image on the right. I’m using vw unit for measurement, so if width of the browser is less, so will be the size of text and image. I also gave flex-wrap, so the text and image divs wrap into rows after certain point.

**App.vue > Menu.vue**

![enter image description here](https://miro.medium.com/max/875/1*KC4AqShhp24QwvtmkagGcQ.png)

Menu bar gives a quick look of the each sections of the page. Its a navbar with unordered list. It takes 40vw of the page on desktop and 100% width on mobile devices.

**Me.vue > Description.vue**

![enter image description here](https://miro.medium.com/max/875/1*_lOOFf4D7jD9k6b4UwcVuA.png)

Its a simple component, with heading, text and list elements. Here as well I used responsive units so its size changes based on the user’s screen resolution.

**Work.vue > FilterTags.vue**

![enter image description here](https://miro.medium.com/max/875/1*094I3UbdG2n4oWWmwFbCdQ.png)

This component is simply a div with text in it.

**Work.vue > ProjectModule.vue**

![enter image description here](https://miro.medium.com/max/875/1*NO3AdZJ1_XjS2A-vjlqIiA.png)

This is the most complex module of this project. But it’s not that complex in general view. When I was reviewing the project structure, I talked about **projectData.js** in assets folder, which is a collection of my project’s details. I’m importing those details here, and sending them to the **ProjectModule.vue** component as props.

```
<ProjectModule
        :title="Object.keys(project).toString()"
        :preview="project[Object.keys(project).toString()].preview_links"
        :type="project[Object.keys(project).toString()].category"
        :read="project[Object.keys(project).toString()].article"
        :coverImage="project[Object.keys(project).toString()].image"
        :content="project[Object.keys(project).toString()].content"
        class="module"
      />
```

**FindMe.vue > FindMeIcons.vue**

![enter image description here](https://miro.medium.com/max/875/1*7ObKZYaYQFZTxMQL9PY1NQ.png)

In FindMe.vue section I have two divs in a flexbox. The right div is a grid with FindMeIcons component. This component is also taking props from FindMe.vue to render the final view.

## Conclusion
This was a week long project and I learned a lot. I always struggled with messy codes and organization, but this project helped to organize my project structure and my logics in a more scientific manner.

Now I also have a better understanding of VueJs. I extensively used its built-in `<transition>` with GSAP library using hooks to get smooth transitions and animations.
In the end, it was a quite a learning adventure which gave me opportunity to learn lots of new things that I was not aware of earlier and I’ll continue this adventure with new projects.
