# Ex.07 Design of Interactive Image Gallery
# Date:
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Magical Flower Gallery</title>

  <style>

    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
      font-family:Verdana, sans-serif;
    }

    body{

      background-image:url('https://images.unsplash.com/photo-1490750967868-88aa4486c946?q=80&w=1600&auto=format&fit=crop');

      background-size:cover;
      background-position:center;
      background-repeat:no-repeat;

      min-height:100vh;

      display:flex;
      justify-content:center;
      align-items:center;

      padding:20px;
      overflow:hidden;
    }

    body::before{

      content:"";

      position:absolute;
      inset:0;

      background:rgba(0,0,0,0.35);

      backdrop-filter:blur(2px);
    }

    .gallery{

      position:relative;
      z-index:1;

      width:90%;
      max-width:1100px;

      background:rgba(255,255,255,0.12);

      border-radius:25px;

      padding:25px;

      backdrop-filter:blur(10px);

      box-shadow:0 0 30px rgba(255,182,255,0.5);

      text-align:center;
    }

    h1{

      color:white;

      font-size:45px;

      margin-bottom:20px;

      text-shadow:
      0 0 10px #ff99ff,
      0 0 20px #ff66cc,
      0 0 40px #cc99ff;
    }

    .main-image{

      width:100%;
      height:500px;

      overflow:hidden;

      border-radius:20px;

      margin-bottom:20px;

      box-shadow:0 0 25px rgba(255,255,255,0.4);
    }

    .main-image img{

      width:100%;
      height:100%;

      object-fit:contain;

      background:black;

      transition:0.5s;
    }

    .thumbnails{

      display:flex;

      justify-content:center;

      flex-wrap:wrap;

      gap:15px;
    }

    .thumbnails img{

      width:150px;

      height:110px;

      object-fit:cover;

      border-radius:15px;

      cursor:pointer;

      transition:0.4s;

      border:3px solid transparent;

      box-shadow:0 0 15px rgba(255,255,255,0.3);
    }

    .thumbnails img:hover{

      transform:scale(1.1);

      border-color:#ffccff;

      box-shadow:0 0 20px #ff99ff;
    }

    .active{

      border-color:yellow !important;

      transform:scale(1.1);
    }

    .buttons{

      margin-top:20px;
    }

    button{

      padding:12px 24px;

      margin:10px;

      border:none;

      border-radius:12px;

      cursor:pointer;

      font-size:18px;

      color:white;

      background:linear-gradient(to right,#ff66cc,#9966ff);

      transition:0.3s;
    }

    button:hover{

      transform:scale(1.08);

      box-shadow:0 0 20px #ff99ff;
    }

    .sparkle{

      position:absolute;

      width:6px;

      height:6px;

      background:white;

      border-radius:50%;

      animation:sparkle 4s linear infinite;

      opacity:0.8;
    }

    @keyframes sparkle{

      0%{
        transform:translateY(0px);
        opacity:0;
      }

      50%{
        opacity:1;
      }

      100%{
        transform:translateY(-800px);
        opacity:0;
      }
    }

  </style>
</head>

<body>

  <!-- Sparkles -->

  <div class="sparkle" style="left:10%; bottom:0;"></div>
  <div class="sparkle" style="left:30%; bottom:-50px;"></div>
  <div class="sparkle" style="left:50%; bottom:-100px;"></div>
  <div class="sparkle" style="left:70%; bottom:-20px;"></div>
  <div class="sparkle" style="left:90%; bottom:-80px;"></div>

  <div class="gallery">

    <h1>✨ Magical Flower Garden ✨</h1>

    <div class="main-image">

      <img id="displayImage"
      src="https://images.unsplash.com/photo-1490750967868-88aa4486c946?q=80&w=1200&auto=format&fit=crop"
      alt="Flower Image">

    </div>

    <div class="thumbnails">

      <!-- Red Rose -->
      <img class="thumb active"
      src="https://images.unsplash.com/photo-1562690868-60bbe7293e94?q=80&w=800&auto=format&fit=crop"
      onclick="changeImage(this)">

      <!-- Pink Rose -->
      <img class="thumb"
      src="flower8.png"
      onclick="changeImage(this)">
      <!-- Pink Lotus Flower -->

      <img class="thumb"
      src="flower7.png"
      onclick="changeImage(this)">

      <!-- Tulip Garden -->
      <img class="thumb"
      src="https://images.unsplash.com/photo-1468327768560-75b778cbb551?q=80&w=800&auto=format&fit=crop"
      onclick="changeImage(this)">

    </div>

    <div class="buttons">

      <button onclick="previousImage()">⬅ Previous</button>

      <button onclick="nextImage()">Next ➡</button>

    </div>

  </div>

  <script>

    const thumbnails =
    document.querySelectorAll(".thumb");

    const displayImage =
    document.getElementById("displayImage");

    let currentIndex = 0;

    function changeImage(element){

      displayImage.src = element.src;

      thumbnails.forEach(img =>
      img.classList.remove("active"));

      element.classList.add("active");

      currentIndex =
      Array.from(thumbnails).indexOf(element);
    }

    function nextImage(){

      currentIndex++;

      if(currentIndex >= thumbnails.length){
        currentIndex = 0;
      }

      changeImage(thumbnails[currentIndex]);
    }

    function previousImage(){

      currentIndex--;

      if(currentIndex < 0){
        currentIndex = thumbnails.length - 1;
      }

      changeImage(thumbnails[currentIndex]);
    }

  </script>

</body>
</html>
```
# OUTPUT:
<img width="1919" height="1139" alt="Screenshot 2026-05-29 001157" src="https://github.com/user-attachments/assets/4cbe49f2-b17a-45b6-a412-4aa338b8aca8" />
<img width="1919" height="1136" alt="Screenshot 2026-05-29 000656" src="https://github.com/user-attachments/assets/807437ed-96a4-45ca-9f7b-ad88423c5911" />
<img width="1919" height="1135" alt="Screenshot 2026-05-29 001236" src="https://github.com/user-attachments/assets/9e7e9cad-6054-487c-9a0e-aead3ba3a362" />
<img width="1919" height="1139" alt="Screenshot 2026-05-29 000727" src="https://github.com/user-attachments/assets/6fd58d17-9963-4f55-aa40-e9bd1bcfa4da" />


# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
