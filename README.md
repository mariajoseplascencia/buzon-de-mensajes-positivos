# buzon-de-mensajes-positivos
elaborado para dejar un mensaje positivo a las personas que lo utilicen
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>💌 TENGO UN MENSAJE PARA TÍ</title>
    
    <style>
        
        body {
            background-image: linear-gradient(135deg, #f0e6ff 0%, #ffe4e9 100%);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            color: #4a4e69; 
        }

        .container {
            background-color: rgba(255, 255, 255, 0.9);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            text-align: center;
            width: 90%;
            max-width: 500px;
        }

        h1 {
            color: #b5838d; 
            font-size: 1.5em;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #a0a4c5;
            margin-bottom: 20px; 
            font-style: italic;
        }

        /* Estilos para el campo de nombre */
        #name-input {
            width: 80%;
            padding: 10px 15px;
            margin-bottom: 25px;
            border: 2px solid #ffcdb2;
            border-radius: 10px;
            font-size: 1em;
            text-align: center;
            outline: none;
            transition: border-color 0.3s;
        }

        #name-input:focus {
            border-color: #ff8e72;
            box-shadow: 0 0 5px rgba(255, 142, 114, 0.5);
        }

        /* Estilos del Buzón */
        #message-box {
            background-color: #ffffff;
            border: 2px solid #ffcdb2; 
            border-radius: 15px;
            min-height: 120px;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            margin-bottom: 30px;
            transition: all 0.5s ease-in-out; 
        }

        #message-text {
            font-size: 1.2em;
            font-weight: 600;
            color: #6d6875; 
            margin: 0;
            line-height: 1.4; 
        }

        /* Estilos del Botón */
        #get-message-btn {
            background-color: #ffb4a2; 
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 30px;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.1s ease;
            box-shadow: 0 5px 15px rgba(255, 180, 162, 0.5);
        }

        #get-message-btn:hover {
            background-color: #ff8e72;
            transform: translateY(-2px);
        }

        #get-message-btn:active {
            transform: translateY(0);
            box-shadow: 0 3px 10px rgba(255, 180, 162, 0.5);
        }

        /* --- CLASES DE ANIMACIÓN --- */
        .fade-out {
            opacity: 0;
            transform: scale(0.95);
            transition: all 0.3s ease; 
        }

        @keyframes fadeInScale {
            0% {
                opacity: 0;
                transform: scale(0.95);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }

        .fade-in {
            animation: fadeInScale 0.5s ease-in-out;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>BIENVENIDO/A✨</h1>
        <p class="subtitle">Primero escribe tu nombre.</p>

        <input type="text" id="name-input" placeholder="Tu Nombre">

        <div id="message-box">
            <p id="message-text">¡DESCUBRE QUE MENSAJE TENGO PARA TÍ!✨.</p>
        </div>

        <button id="get-message-btn">HAZ CLICK AQUÍ</button>
    </div>

    <script>
     

        // Mensajes genéricos (plantillas)
        const messages = [
             ", que la paz que sobrepasa todo entendimiento inunde tu corazón hoy.",
            ", tu valor no depende de tus logros. Eres amada/o incondicionalmente.",
            ", el sol de hoy trae nuevas oportunidades. Confía en el proceso.",
            ", eres un ser de luz en constante crecimiento. No te rindas jamás.",
            ", detente un momento y siente la gratitud. ¡Tienes mucho por lo que celebrar!",
            ", la fuerza para superar este desafío ya reside dentro de ti.",
            ", todo tiene un tiempo. Ten paciencia y sigue sembrando con amor.",
            ", hoy es un buen día para ser amable contigo misma/o. Eres suficiente.",
            ", recuerda quién eres: un/a hijo/a amada/o con un propósito divino.",
            ", suelta lo que no puedes controlar y abraza la serenidad.",
            ", cree en la magia de los nuevos comienzos. ¡Este es el tuyo!",
            ", cada paso que das, por pequeño que sea, te acerca a tu meta.",
            ", que la luz de Dios ilumine cada rincón de tu día.",
            ", tu corazón es fuerte y capaz de superar cualquier desafío.",
            ", recuerda que eres amado/a más allá de lo que puedas imaginar.",
            ", cada momento es una oportunidad para crecer y aprender.",
            ", que la esperanza guíe cada uno de tus pasos hoy.",
            ", respira hondo y permite que la paz llene tu alma.",
            ", cada día es un regalo. Disfruta de sus pequeños milagros.",
            ", eres valiosa/o tal como eres, sin necesidad de compararte.",
            ", la alegría se encuentra en las cosas simples. Ábrete a ella.",
            ", confía en que Dios tiene planes perfectos para ti.",
            ", tu sonrisa puede iluminar incluso los días más grises.",
            ", suelta el miedo y abraza la confianza en el proceso divino.",
            ", eres capaz de cosas increíbles. Cree en ti misma/o.",
            ", hoy es un buen día para sembrar bondad y gratitud.",
            ", recuerda que cada desafío trae consigo una lección valiosa.",
            ", tu alma es fuerte, incluso cuando el camino se siente difícil.",
            ", que la paciencia te acompañe y la serenidad te guíe.",
            ", permite que la gratitud transforme tu perspectiva del día.",
            ", eres amado/a incondicionalmente, justo como eres ahora.",
            ", cada paso que das con intención te acerca a tu propósito.",
            ", confía en tu intuición; Dios te habla a través de ella.",
            ", que la calma y la claridad llenen tu mente hoy.",
            ", tu fuerza interior es más grande de lo que crees.",
            ", suelta lo que pesa y abre espacio para lo que te nutre.",
            ", cada amanecer trae nuevas oportunidades y bendiciones.",
            ", la fe en ti misma/o puede mover montañas.",
            ", recuerda que eres un ser único y valioso para el mundo.",
            ", que la gratitud sea tu guía y la alegría tu compañera.",
            ", los pequeños pasos también cuentan; sigue avanzando.",
            ", tu corazón sabe lo que necesita. Escúchalo con amor.",
            ", hoy es un buen día para perdonarte y avanzar con ligereza.",
            ", eres luz en los lugares donde más se necesita.",
            ", confía en que todo llega a su tiempo perfecto.",
            ", cada respiración consciente te acerca a la paz interior.",
            ", tu alma es valiosa y merece amor, cuidado y respeto.",
            ", la esperanza nunca se pierde cuando crees en lo bueno.",
            ", permite que tu corazón se llene de alegría sin culpa.",
            ", cada acto de bondad regresa a ti multiplicado.",
            ", suelta lo que te detiene y avanza con fe.",
            ", recuerda que todo desafío es una oportunidad disfrazada.",
            ", eres guiada/o por la luz y la sabiduría divina.",
            ", confía en que el amor y la paz están siempre cerca de ti.",
            ", cada día trae nuevos motivos para agradecer y sonreír.",
            ", tu corazón tiene la fuerza para sanar y renovarse.",
            ", permite que la serenidad sea tu refugio hoy.",
            ", eres un reflejo de bondad, luz y amor en este mundo.",
            ", confía en que lo mejor está por venir, incluso si aún no lo ves.",
            ", tu vida está llena de momentos preciosos; no los pases por alto.",
            ", cada pensamiento positivo siembra semillas de alegría y paz.",
            ", cree en ti misma/o, en tu propósito y en los planes de Dios para ti."
        ];


     
        const danielMessage = "confía en Dios...lo que tu corazón anhela esta más cerca de lo que imaginas.";

        // 1. Obtener los elementos del DOM
        const nameInput = document.getElementById('name-input');
        const messageText = document.getElementById('message-text');
        const getMessageBtn = document.getElementById('get-message-btn');
        const messageBox = document.getElementById('message-box');

        // 2. Función para obtener un mensaje aleatorio
        function getRandomMessage() {
            const randomIndex = Math.floor(Math.random() * messages.length);
            return messages[randomIndex];
        }

        function displayMessage() {

            let rawName = nameInput.value.trim();
            let lowerName = rawName.toLowerCase();
            
            let fullMessage = "";
            let capitalizedName = "";
                  if (lowerName === "daniel") {
                fullMessage = `¡Hola Daniel! ${danielMessage}`;
            } 
            else if (rawName === "") {
                // *** CASO VACÍO ***
                fullMessage = `¡Hola Querido/a colega pedagogo/a! ${getRandomMessage()}`;
            } 
            else {
                capitalizedName = rawName.charAt(0).toUpperCase() + rawName.slice(1).toLowerCase();
                
                const randomMessageTemplate = getRandomMessage();
                fullMessage = `¡Hola ${capitalizedName}! ${randomMessageTemplate}`;
            }
            // -------------------------------------------

            // Aplicar animación de 'salida' (fade-out)
            messageBox.classList.remove('fade-in'); 
            messageBox.classList.add('fade-out');

            // Esperar el tiempo de la animación de salida (300ms)
            setTimeout(() => {
                // Actualizar el texto del mensaje (usamos innerHTML para la negrita del mensaje de Daniel)
                messageText.innerHTML = fullMessage; 

                // Quitar la clase de salida y añadir la de entrada (fade-in)
                messageBox.classList.remove('fade-out');
                messageBox.classList.add('fade-in');
                
                // Eliminar la clase de entrada después de que termine la animación (500ms)
                setTimeout(() => {
                    messageBox.classList.remove('fade-in');
                }, 500);
                
            }, 300);
        }

        // 4. Escuchar el evento click del botón
        getMessageBtn.addEventListener('click', displayMessage);
    </script>
</body>
</html>
