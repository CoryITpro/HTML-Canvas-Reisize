<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://canvas-resize.netlify.app/">
    <img src="screen.png" alt="Logo" width="900px" height="600px">
  </a>

  <h3 align="center">HTML CANVAS RESIZE TEST</h3>

  <p align="center">
    An awesome HTML CANVAS ratio test!
    <br />
    <a href="https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://canvas-resize.netlify.app/">View Demo</a>
    ·
    <a href="https://github.com/CoryITpro/HTML-Canvas-Reisize/issues">Report Bug</a>
    ·
    <a href="https://github.com/CoryITpro/HTML-Canvas-Reisize/issues">Request Feature</a>
  </p>
</div>
<!-- ABOUT THE PROJECT -->

# About The UI

-   Main Canvas `containing the red circle`.
-   Two sliders `right one control the height of the canvas - and bottom one is for the width`.
-   The text - `Displays the pixel ratio of the canvas`.

# About the script function

## initializing

      const ratio = { width: 200, height: 100 };

This is the initial value of canvas ratio.

## draw function `main core of this project`.

-   first calculate the pixel ratio of window and canvas for the comparison.

          const windowRatio = window.innerWidth / window.innerHeight;
          const canvasRatio = ratio.width / ratio.height;

-   compare ratios
-   when canvasRatio > windowRatio

    <img src="high.png" alt="Logo" >

          c.style.width = `80vw`;
          const height = 90 / canvasRatio;
          c.style.height = `${height}vw`;

-   when canvasRatio < windowRatio

    <img src="wide.png" alt="Logo" >

          c.style.height = `90vh`;
          const width = 80 \* canvasRatio;
          c.style.width = `${width}vh`;

-   clear the canvas

          ctx.clearRect(0, 0, 1000, 1000);

-   redraw the circle

          ctx.beginPath();
          ctx.lineWidth = 55;
          ctx.strokeStyle = "red";
          ctx.arc(500, 500, 420, 0, 2 \* Math.PI);
          ctx.stroke();
          ctx.save();

-   redraw the ratio text

          text.innerHTML = `${ratio.width}X${ratio.height}`;

## event listenders `user control`.

-   once you make change in the right side slider

          document.querySelector("#range2").addEventListener("input", (event) => {
            ratio.height = event.target.value;
            draw();
          });

-   once you make change in the bottom side slider

          document.querySelector("#range1").addEventListener("input", (event) => {
              ratio.width = event.target.value;
              draw();
          });

-   and add event of resizing the browser window.

          window.addEventListener("resize", () => {
              draw();
          });
