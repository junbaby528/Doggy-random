<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Random Dog Image</title>
  <style>
    body {
      background-color:pink;
      font-family: Arial, sans-serif;
      text-align: center;
      margin-top: 50px;
    }
    img {
      margin-top: 20px;
      width: 300px;
      height: auto;
      border: 2px solid #ccc;
      border-radius: 10px;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <marquee width ="100%"
  behavior = "alternate"
  bgcolor = "green">
 <h1>Random Dog Image Generator</h1>
 </marquee>
  
  <button id="fetchButton">Get Random Dog Image</button>
  <br>
  <img src="" alt="Random dog" id="Imgcontainer">
  
  <script>
    
    function next() {
      const img = document.getElementById('Imgcontainer'); 
      fetch('https://dog.ceo/api/breeds/image/random') 
        .then(response => {
          if (!response.ok) {
            throw new Error('Network response was not ok');
          }
          return response.json();
        })
        .then(data => {
          img.src = data.message; 
        })
        .catch(error => {
          console.error('Error fetching data:', error); 
        });
    }

    
    document.getElementById('fetchButton').addEventListener('click', next);
  </script>
</body>
</html>
