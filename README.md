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
    </style>
</head>
<body>
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

    <script>
        function showPainInfo(area) {
            let title = "";
            let description = "";
            let whatsappMessage = encodeURIComponent("Hola, tengo dolor en la " + area + ". ¿Podría agendar una consulta?");
            let whatsappLink = "https://wa.me/3412636248?text=" + whatsappMessage;
            
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
    </script>
</body>
</html>
