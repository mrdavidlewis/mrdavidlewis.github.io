---
title: "Visualise a set of colours"
date: 2022-11-02T14:23:04Z
draft: false
---

See an example:


[Below implemented](/examples/show_colours.html)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>IVP Colours</title>

  <style>
    #main-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }

  .colour-item {
    margin: 1rem;
    padding: 1rem;
    width: 10rem;
    text-align: center;
    margin-right: 1rem;
    border: 0px solid khaki;
    border-radius: .5rem;
  }
  </style>

</head>
<body>
  <h1>IVP Colours</h1>
  <div id="main-container">
  </div>
</body>

<script>

  function write_colours() {
    let mycolors = [['rgb(180,180,180)'],
            ['rgb(199,51,100)'],
            ['rgb(199,51,54)'],
            ['rgb(247,137,42)'],
            ['rgb(251,104,39)'],
            ['rgb(103,106,204)'],
            ['rgb(147,204,224)'],
            [ 'rgb(121,184,255)'],
            ['rgb(229, 240, 224)'],
            ['rgb(61, 56, 56)'],
            ['rgb(84, 144, 136)'],
            ['rgb(0, 100, 0, .2)'],
            ['#547575', 'slider'],
            ['rgb(150,150,150)', 'slider pip'],
            ['#ffed00', 'pip-active:'],
            ['rgb(230,230,230', 'env colour']
          ]

    let mainContainerElement = document.querySelector("#main-container");

    for (let i = 0; i < mycolors.length; i++) {
      let temp = mainContainerElement.appendChild(document.createElement('div'));
      temp.setAttribute('class', 'colour-item');
      temp.style.background = mycolors[i][0];
      if (Array.isArray(mycolors[i])){
        let colorName = temp.appendChild(document.createElement('p'));
        colorName.textContent = mycolors[i][0];
        if (mycolors[i].length > 1) {
          let colorDescription = temp.appendChild(document.createElement('p'))
          colorDescription.textContent = mycolors[i][1];
        }
      }
    }
  }

  write_colours();


</script>
```