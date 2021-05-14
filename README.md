# 3D-visualization-elements-on-hover-using-html-css
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>repl.it</title>
    <link href="style.css" rel="stylesheet" type="text/css" />
  </head>
  <body>
    <script src="script.js"></script>
    <html lang="en" >
<head>
  <meta charset="UTF-8">
  <title>3D Visualization | Webdevtrick.com</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.min.css">
  <link rel="stylesheet" href="style.css">
 
</head>
<body>
<h1 class="title">Hover the elements</h1>
<div class="container">
  <div>
    <p>Header Section</p>
    <section>
      <header>
        <h1>H1 in section header</h1>
      </header>
      <p>Paragraph in section</p>
      <footer>
        <p>Paragraph in section footer</p>
      </footer>
    </section>
    <p>Footer Section.</p>
    <p>Copyright Section.</p>
  </div>
</div>
  </body>
</html>
.....css.....
:root {
  -webkit-perspective: 500vmin;
          perspective: 500vmin;
  --side-height: 1.5em;
  --default-color: rgba(23, 74, 243, 0.575);
  --hover-color: rgba(28, 211, 224, 0.2);
  --transform-duration: .3s;
}
 
body {
  min-height: 100vh;
  font: normal 1em/1.4 helvetica, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
 
.title {
  font: 100 2em/1.5 helvetica, sans-serif;
}
 
.container {
  -webkit-transform-style: preserve-3d;
          transform-style: preserve-3d;
  -webkit-transform: rotateY(-40deg) rotateX(40deg);
          transform: rotateY(-40deg) rotateX(40deg);
}
.container * {
  display: block;
  padding: 1em;
  margin: .5em;
  position: relative;
  background: var(--default-color);
  -webkit-transform-style: preserve-3d;
          transform-style: preserve-3d;
  -webkit-transform: translateZ(0);
          transform: translateZ(0);
  transition: -webkit-transform var(--transform-duration);
  transition: transform var(--transform-duration);
  transition: transform var(--transform-duration), -webkit-transform var(--transform-duration);
}
.container *::before, .container *::after {
  content: "";
  display: block;
  position: absolute;
  background: transparent;
  transition: all var(--transform-duration);
}
.container *::before {
  width: 100%;
  height: var(--side-height);
  left: 0;
  bottom: 0;
  -webkit-transform-origin: center bottom;
          transform-origin: center bottom;
  -webkit-transform: scaleY(0) rotateX(90deg);
          transform: scaleY(0) rotateX(90deg);
}
.container *::after {
  width: var(--side-height);
  height: 100%;
  right: 0;
  top: 0;
  -webkit-transform-origin: right center;
          transform-origin: right center;
  -webkit-transform: scaleX(0) rotateY(-90deg);
          transform: scaleX(0) rotateY(-90deg);
}
.container *:hover {
  background: var(--hover-color);
  -webkit-transform: translateZ(var(--side-height));
          transform: translateZ(var(--side-height));
}
.container *:hover::before, .container *:hover::after {
  background: var(--hover-color);
}
.container *:hover::before {
  -webkit-transform: scaleY(1) rotateX(90deg);
          transform: scaleY(1) rotateX(90deg);
}
.container *:hover::after {
  -webkit-transform: scaleX(1) rotateY(-90deg);
          transform: scaleX(1) rotateY(-90deg);
}
.container *:empty {
  display: none;
}
