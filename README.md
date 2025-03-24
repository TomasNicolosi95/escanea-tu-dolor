<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Escanea tu Dolor</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
            background-color: #f0f0f0;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            margin: auto;
        }
        .body-map {
            width: 300px;
            margin: auto;
            cursor: pointer;
        }
        .pain-info {
            display: none;
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ddd;
            background-color: #f9f9f9;
            border-radius: 5px;
        }
        .whatsapp-button {
            display: inline-block;
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #25D366;
            color: white;
            text-decoration: none;
            font-size: 18px;
            border-radius: 5px;
        }
        .contact-form {
            margin-top: 20px;
            padding: 10px;
            background: #fff;
            border-radius: 5px;
            box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
        }
        .contact-form input, .contact-form textarea {
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        .contact-form button {
            background-color: #007BFF;
            color: white;
            border: none;
            padding: 10px;
            width: 100%;
            border-radius: 5px;
            cursor: pointer;
        }
        .contact-form button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Escanea tu Dolor</h2>
        <p>Toca la zona donde sientes dolor:</p>
        <img src="https://upload.wikimedia.org/wikipedia/commons/6/64/Human_body_silhouette.png" class="body-map" usemap="#bodymap">
        
        <map name="bodymap">
            <area shape="rect" coords="120,20,180,80" alt="Cabeza" onclick="showPainInfo('cabeza')">
            <area shape="rect" coords="110,80,190,150" alt="Espalda" onclick="showPainInfo('espalda')">
            <area shape="rect" coords="120,160,180,220" alt="Rodilla" onclick="showPainInfo('rodilla')">
        </map>
        
        <div id="pain-info" class="pain-info">
            <h3 id="pain-title"></h3>
            <p id="pain-description"></p>
            <a id="whatsapp-link" class="whatsapp-button" target="_blank">Agendar consulta por WhatsApp</a>
        </div>
        
        <div class="contact-form">
            <h3>Déjanos tu consulta</h3>
            <input type="text" id="name" placeholder="Tu nombre" required>
            <input type="email" id="email" placeholder="Tu correo" required>
            <textarea id="message" placeholder="Describe tu dolor" required></textarea>
            <button onclick="sendMessage()">Enviar</button>
        </div>
    </div>
    
    <script>
        function showPainInfo(area) {
            let title = "";
            let description = "";
            let whatsappMessage = encodeURIComponent("Hola, tengo dolor en la " + area + ". ¿Podría agendar una consulta?");
            let whatsappLink = "https://wa.me/TU_NUMERO?text=" + whatsappMessage;
            
            switch(area) {
                case 'cabeza':
                    title = "Dolor de Cabeza";
                    description = "Puede estar relacionado con tensión muscular o estrés. Relájate y agenda una consulta.";
                    break;
                case 'espalda':
                    title = "Dolor de Espalda";
                    description = "Suele deberse a malas posturas o sobrecarga. Te ayudamos a corregirlo.";
                    break;
                case 'rodilla':
                    title = "Dolor de Rodilla";
                    description = "Puede ser por sobrecarga o mala alineación. Consulta para un diagnóstico preciso.";
                    break;
            }
            
            document.getElementById("pain-title").innerText = title;
            document.getElementById("pain-description").innerText = description;
            document.getElementById("whatsapp-link").href = whatsappLink;
            document.getElementById("pain-info").style.display = "block";
        }
        
        function sendMessage() {
            let name = document.getElementById("name").value;
            let email = document.getElementById("email").value;
            let message = document.getElementById("message").value;
            
            if (name && email && message) {
                alert("Gracias, " + name + "! Nos pondremos en contacto contigo pronto.");
            } else {
                alert("Por favor, completa todos los campos.");
            }
        }
    </script>
</body>
</html>
