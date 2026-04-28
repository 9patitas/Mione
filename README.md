
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mione Chatbot - Postres para Mascotas</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f0f7ff;
            color: #333;
            line-height: 1.6;
            padding: 20px;
            background-image: radial-gradient(#5f82a233 1px, transparent 1px);
            background-size: 20px 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        header {
            background: linear-gradient(135deg, #5F82A2 0%, #4a6c8a 100%);
            color: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(95, 130, 162, 0.3);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: "🐾 🐾 🐾";
            position: absolute;
            top: 10px;
            left: 10px;
            opacity: 0.2;
            font-size: 24px;
        }

        header::after {
            content: "🐾 🐾 🐾";
            position: absolute;
            bottom: 10px;
            right: 10px;
            opacity: 0.2;
            font-size: 24px;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }

        .logo-icon {
            font-size: 2rem;
        }

        .tagline {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 15px;
        }

        .mascot-info {
            background-color: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .mascot-info h2 {
            color: #5F82A2;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #5F82A2;
        }

        input {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        input:focus {
            outline: none;
            border-color: #5F82A2;
        }

        .btn {
            background-color: #5F82A2;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .btn:hover {
            background-color: #4a6c8a;
            transform: translateY(-2px);
            box-shadow: 0 5px 10px rgba(95, 130, 162, 0.3);
        }

        .btn-secondary {
            background-color: #8a9ba8;
        }

        .btn-secondary:hover {
            background-color: #6c7d8a;
        }

        .chat-section {
            display: flex;
            gap: 25px;
            flex-wrap: wrap;
        }

        .chat-container {
            flex: 1;
            min-width: 300px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        .chat-header {
            background: linear-gradient(135deg, #5F82A2 0%, #4a6c8a 100%);
            color: white;
            padding: 20px;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .chat-header i {
            font-size: 1.5rem;
        }

        .chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            max-height: 500px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .message {
            padding: 15px;
            border-radius: 10px;
            max-width: 80%;
            position: relative;
        }

        .bot-message {
            background-color: #f0f7ff;
            border-left: 4px solid #5F82A2;
            align-self: flex-start;
        }

        .bot-message::before {
            content: "Mione:";
            font-weight: 600;
            color: #5F82A2;
            display: block;
            margin-bottom: 5px;
        }

        .user-message {
            background-color: #e8f0fe;
            border-right: 4px solid #4a6c8a;
            align-self: flex-end;
        }

        .user-message::before {
            content: "Tú:";
            font-weight: 600;
            color: #4a6c8a;
            display: block;
            margin-bottom: 5px;
        }

        .menu-options {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .menu-option {
            background-color: white;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            gap: 10px;
        }

        .menu-option:hover {
            border-color: #5F82A2;
            transform: translateY(-3px);
            box-shadow: 0 5px 10px rgba(95, 130, 162, 0.2);
        }

        .menu-option i {
            font-size: 1.8rem;
            color: #5F82A2;
        }

        .results-container {
            flex: 1;
            min-width: 300px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        .results-header {
            background: linear-gradient(135deg, #5F82A2 0%, #4a6c8a 100%);
            color: white;
            padding: 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .results-content {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            max-height: 500px;
        }

        .postre-card {
            background-color: #f9f9f9;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
            border-left: 4px solid #5F82A2;
        }

        .postre-card h4 {
            color: #5F82A2;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .postre-card p {
            margin-bottom: 5px;
        }

        .pet-info-display {
            background-color: #f0f7ff;
            border-radius: 10px;
            padding: 20px;
            margin-top: 20px;
        }

        .pet-info-display h3 {
            color: #5F82A2;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .info-row {
            display: flex;
            margin-bottom: 10px;
        }

        .info-label {
            font-weight: 600;
            width: 150px;
            color: #5F82A2;
        }

        .info-value {
            flex: 1;
        }

        .navigation-buttons {
            display: flex;
            gap: 10px;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .footer {
            text-align: center;
            margin-top: 20px;
            padding: 20px;
            color: #666;
            font-size: 0.9rem;
        }

        .highlight {
            color: #5F82A2;
            font-weight: 600;
        }

        .emoji {
            font-size: 1.2rem;
        }

        .counter-badge {
            background-color: #5F82A2;
            color: white;
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 0.8rem;
            margin-left: 5px;
        }

        @media (max-width: 768px) {
            .chat-section {
                flex-direction: column;
            }
            
            h1 {
                font-size: 2rem;
            }
            
            .menu-options {
                grid-template-columns: 1fr;
            }
            
            .results-header {
                flex-direction: column;
                gap: 10px;
                align-items: flex-start;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-paw logo-icon"></i> Mione Chatbot <span class="emoji">😊</span></h1>
            <p class="tagline">Postres deliciosos para tu mascota - ¡Asistencia personalizada!</p>
            <p>Hola, soy Mione, tu asistente virtual. Estoy aquí para ayudarte de una manera rápida y amigable.</p>
        </header>

        <section class="mascot-info">
            <h2><i class="fas fa-paw"></i> Información de tu mascota</h2>
            <p>Para ofrecerte una experiencia personalizada, necesito conocer a tu mascota.</p>
            
            <div class="form-group">
                <label for="petName"><i class="fas fa-dog"></i> ¿Cuál es el nombre de tu mascota?</label>
                <input type="text" id="petName" placeholder="Ej: Max, Luna, Toby...">
            </div>
            
            <div class="form-group">
                <label for="petType"><i class="fas fa-cat"></i> ¿Qué tipo de mascota es?</label>
                <input type="text" id="petType" placeholder="Ej: perro, gato, conejo, etc.">
            </div>
            
            <div class="form-group">
                <label for="petBirthday"><i class="fas fa-birthday-cake"></i> ¿Cuándo es su cumpleaños? (DD/MM/AAAA)</label>
                <input type="text" id="petBirthday" placeholder="Ej: 15/04/2018">
            </div>
            
            <div class="navigation-buttons">
                <button id="savePetInfo" class="btn">
                    <i class="fas fa-save"></i> Guardar información
                </button>
                <button id="resetForm" class="btn btn-secondary">
                    <i class="fas fa-redo"></i> Limpiar formulario
                </button>
            </div>
        </section>

        <section class="chat-section">
            <div class="chat-container">
                <div class="chat-header">
                    <i class="fas fa-comments"></i>
                    <h3>Chat con Mione</h3>
                </div>
                <div class="chat-messages" id="chatMessages">
                    <div class="message bot-message">
                        ¡Hola! Soy Mione 😊. Por favor, ingresa la información de tu mascota primero para poder ayudarte.
                    </div>
                </div>
            </div>

            <div class="results-container">
                <div class="results-header">
                    <div style="display: flex; align-items: center; gap: 10px;">
                        <i class="fas fa-search"></i>
                        <h3>Resultados y Recomendaciones</h3>
                    </div>
                    <button id="backToMenu" class="btn btn-secondary" style="display: none;">
                        <i class="fas fa-home"></i> Volver al menú
                    </button>
                </div>
                <div class="results-content" id="resultsContent">
                    <p>Aquí aparecerán las recomendaciones de postres para tu mascota.</p>
                    <p>Por favor, completa la información de tu mascota para comenzar.</p>
                </div>
            </div>
        </section>

        <div class="menu-options" id="menuOptions" style="display: none;">
            <div class="menu-option" id="option1">
                <i class="fas fa-paw"></i>
                <h4>Recomendaciones personalizadas</h4>
                <p>Postres seleccionados especialmente para tu mascota</p>
            </div>
            <div class="menu-option" id="option2">
                <i class="fas fa-search"></i>
                <h4>Buscar por tipo de postre</h4>
                <p>Encuentra postres por categoría</p>
            </div>
            <div class="menu-option" id="option3">
                <i class="fas fa-list"></i>
                <h4>Ver todos los postres <span class="counter-badge">50</span></h4>
                <p>Nuestro catálogo completo</p>
            </div>
            <div class="menu-option" id="option4">
                <i class="fas fa-info-circle"></i>
                <h4>Información de tu mascota</h4>
                <p>Ver datos y recomendaciones especiales</p>
            </div>
            <div class="menu-option" id="option5">
                <i class="fas fa-sign-out-alt"></i>
                <h4>Salir del sistema</h4>
                <p>Finalizar la sesión con Mione</p>
            </div>
        </div>

        <div class="footer">
            <p><span class="highlight">Nueve Patitas</span> - Postres deliciosos y saludables para tu mejor amigo 🐾</p>
            <p>Chatbot Mione - Asistente virtual especializado en nutrición para mascotas</p>
            <p><strong>50 postres disponibles</strong> - Puedes volver al menú principal en cualquier momento 😊</p>
        </div>
    </div>

    <script>
        // Base de datos completa de 50 postres (según tu código C++)
        const postres = [
            // ID 1-10
            {id: 1, tipo: "CUPCAKE", nombre: "PUPPAKE PIPO", sabor: "ZANAHORIA Y AVENA"},
            {id: 2, tipo: "DONA", nombre: "PUGGI DONUTS", sabor: "MANZANA Y CANELA"},
            {id: 3, tipo: "GALLETA", nombre: "GUDI BONES", sabor: "MIEL Y AVENA"},
            {id: 4, tipo: "HELADO", nombre: "BUBUJA ICE CREAM", sabor: "PLÁTANO Y MANTEQUILLA DE MANÍ"},
            {id: 5, tipo: "MUFFIN", nombre: "YAKY MUFFIN", sabor: "CALABAZA"},
            {id: 6, tipo: "SNACK", nombre: "CELESTE TREATS", sabor: "AVENA Y PLÁTANO"},
            {id: 7, tipo: "PASTEL", nombre: "BLANCA CAKE", sabor: "POLLO Y CAMOTE"},
            {id: 8, tipo: "GALLETA", nombre: "BIANCA BITES", sabor: "CACAHUATE"},
            {id: 9, tipo: "PALETA HELADA", nombre: "MORITA POPS", sabor: "YOGURT Y FRESA"},
            {id: 10, tipo: "GALLETA", nombre: "PIPO CRUNCH", sabor: "ZANAHORIA Y MIEL"},
            
            // ID 11-20
            {id: 11, tipo: "ROLLITO", nombre: "PUGGI ROLL", sabor: "AVENA Y PLÁTANO"},
            {id: 12, tipo: "BARRITA", nombre: "GUDI BAR", sabor: "AVENA"},
            {id: 13, tipo: "HELADO", nombre: "BURBUJA BERRY CUP", sabor: "ARÁNDANO"},
            {id: 14, tipo: "TARTALETA", nombre: "YAKY PIE", sabor: "MANZANA"},
            {id: 15, tipo: "BROWNIE", nombre: "CELESTE CHOCO", sabor: "ALGARROBO"},
            {id: 16, tipo: "HELADO", nombre: "BLANCA YOGUPAW", sabor: "YOGURT NATURAL"},
            {id: 17, tipo: "WAFFLE", nombre: "BIANCA WOOFLIE", sabor: "AVENA Y MIEL"},
            {id: 18, tipo: "GALLETA", nombre: "MORITA COOKIE", sabor: "FRESA Y AVENA"},
            {id: 19, tipo: "GALLETA", nombre: "PIPO HONEY BONES", sabor: "MIEL"},
            {id: 20, tipo: "MUFFIN", nombre: "PUGGI MUFFCAKE", sabor: "CALABAZA"},
            
            // ID 21-30
            {id: 21, tipo: "HELADO", nombre: "GUDI ICE BITE", sabor: "PLÁTANO"},
            {id: 22, tipo: "CUPCAKE", nombre: "BURBUJA CUPCAKE", sabor: "COCO"},
            {id: 23, tipo: "GALLETA", nombre: "YAKI CRUNCHIES", sabor: "MANZANA"},
            {id: 24, tipo: "GALLETA", nombre: "CELESTE BONE MIX", sabor: "MANZANA"},
            {id: 25, tipo: "PASTEL", nombre: "BLANCA BLISS CAKE", sabor: "POLLO Y AVENA"},
            {id: 26, tipo: "CREMOSO", nombre: "BIANCA CREAM PAW", sabor: "MANGO"},
            {id: 27, tipo: "DONA", nombre: "MORITA DONUT", sabor: "YOGURT"},
            {id: 28, tipo: "BARRITA", nombre: "PIPO CHEWY BAR", sabor: "MIEL Y AVENA"},
            {id: 29, tipo: "TARTALETA", nombre: "PUGGI TART", sabor: "MANZANA"},
            {id: 30, tipo: "PALETA HELADA", nombre: "GUDI POSICLE", sabor: "PLÁTANO"},
            
            // ID 31-40
            {id: 31, tipo: "CREMOSO", nombre: "BURBUJA PUDDING", sabor: "YOGURT Y COCO"},
            {id: 32, tipo: "GALLETA", nombre: "YAKY BONES DELUXE", sabor: "MANTEQUILLA DE MANÍ"},
            {id: 33, tipo: "TARTALETA", nombre: "CELESTE PIE", sabor: "FRESA"},
            {id: 34, tipo: "MUFFIN", nombre: "CELESTE CRUNCH", sabor: "PLÁTANO"},
            {id: 35, tipo: "BROWNIE", nombre: "BIANCA BROWNIE", sabor: "AVENA"},
            {id: 36, tipo: "SNACK", nombre: "MORITA TREATS", sabor: "FRESA Y YOGURT"},
            {id: 37, tipo: "HELADO", nombre: "PIPO ICE BAR", sabor: "MANGO"},
            {id: 38, tipo: "GALLETA", nombre: "PUGGI COOKIE PAW", sabor: "AVENA"},
            {id: 39, tipo: "PASTEL", nombre: "GUDI CAKE MINI", sabor: "CAMOTE"},
            {id: 40, tipo: "GALLETA", nombre: "BURBUJA BONES", sabor: "COCO"},
            
            // ID 41-50
            {id: 41, tipo: "PALETA HELADA", nombre: "YAKY YOGURT POP", sabor: "YOGURT NATURAL"},
            {id: 42, tipo: "GALLETA", nombre: "CELESTE CRUNCH", sabor: "MANZANA"},
            {id: 43, tipo: "DONA", nombre: "BLANCA DONUT DELUXE", sabor: "MIEL"},
            {id: 44, tipo: "GALLETA", nombre: "BIANCA HONEY PAW", sabor: "MIEL"},
            {id: 45, tipo: "PASTEL", nombre: "MORITA BERRY CAKE", sabor: "FRESA"},
            {id: 46, tipo: "BOLITAS", nombre: "PIPO PUFFS", sabor: "AVENA Y PLÁTANO"},
            {id: 47, tipo: "TARTALETA", nombre: "PUGGI PIE MINI", sabor: "ZANAHORIA"},
            {id: 48, tipo: "DONA", nombre: "GUDI DONUT CRUNCH", sabor: "MANÍ"},
            {id: 49, tipo: "CREMOSO", nombre: "BURBUJA CREAM PAW", sabor: "YOGURT"},
            {id: 50, tipo: "PASTEL", nombre: "YAKY CELEBRATION CAKE", sabor: "POLLO Y MANZANA"}
        ];

        // Información de la mascota
        let mascotaInfo = {
            nombre: "",
            tipo: "",
            cumpleanos: "",
            edad: 0
        };

        // Estado de la aplicación
        let currentView = 'menu';

        // Elementos DOM
        const petNameInput = document.getElementById('petName');
        const petTypeInput = document.getElementById('petType');
        const petBirthdayInput = document.getElementById('petBirthday');
        const savePetInfoBtn = document.getElementById('savePetInfo');
        const resetFormBtn = document.getElementById('resetForm');
        const backToMenuBtn = document.getElementById('backToMenu');
        const chatMessages = document.getElementById('chatMessages');
        const resultsContent = document.getElementById('resultsContent');
        const menuOptions = document.getElementById('menuOptions');

        // Función para agregar mensajes al chat
        function addMessage(sender, message, isBot = true) {
            const messageDiv = document.createElement('div');
            messageDiv.className = isBot ? 'message bot-message' : 'message user-message';
            messageDiv.innerHTML = message;
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        // Función para calcular la edad de la mascota
        function calcularEdadMascota(cumpleanos) {
            const parts = cumpleanos.split('/');
            if (parts.length !== 3) return 0;
            
            const dia = parseInt(parts[0]);
            const mes = parseInt(parts[1]) - 1;
            const anio = parseInt(parts[2]);
            
            const hoy = new Date();
            const cumple = new Date(anio, mes, dia);
            
            let edad = hoy.getFullYear() - cumple.getFullYear();
            const mesDiff = hoy.getMonth() - cumple.getMonth();
            
            if (mesDiff < 0 || (mesDiff === 0 && hoy.getDate() < cumple.getDate())) {
                edad--;
            }
            
            return edad;
        }

        // Función para mostrar el menú principal
        function mostrarMenuPrincipal() {
            currentView = 'menu';
            backToMenuBtn.style.display = 'none';
            
            // Mostrar mensaje en el chat
            addMessage('bot', '¿En qué más puedo ayudarte? Selecciona una opción del menú. 😊');
            
            // Mostrar contenido del menú
            resultsContent.innerHTML = `
                <h3><i class="fas fa-home"></i> Menú Principal</h3>
                <p>Hola de nuevo ${mascotaInfo.nombre ? mascotaInfo.nombre + '!' : '!'} 😊</p>
                <p>Selecciona una de las siguientes opciones:</p>
                <div class="menu-options" style="display: grid; margin-top: 20px;">
                    <div class="menu-option" onclick="seleccionarOpcion(1)">
                        <i class="fas fa-paw"></i>
                        <h4>Recomendaciones personalizadas</h4>
                        <p>Postres seleccionados especialmente para tu mascota</p>
                    </div>
                    <div class="menu-option" onclick="seleccionarOpcion(2)">
                        <i class="fas fa-search"></i>
                        <h4>Buscar por tipo de postre</h4>
                        <p>Encuentra postres por categoría</p>
                    </div>
                    <div class="menu-option" onclick="seleccionarOpcion(3)">
                        <i class="fas fa-list"></i>
                        <h4>Ver todos los postres <span class="counter-badge">50</span></h4>
                        <p>Nuestro catálogo completo</p>
                    </div>
                    <div class="menu-option" onclick="seleccionarOpcion(4)">
                        <i class="fas fa-info-circle"></i>
                        <h4>Información de tu mascota</h4>
                        <p>Ver datos y recomendaciones especiales</p>
                    </div>
                    <div class="menu-option" onclick="seleccionarOpcion(5)">
                        <i class="fas fa-sign-out-alt"></i>
                        <h4>Salir del sistema</h4>
                        <p>Finalizar la sesión con Mione</p>
                    </div>
                </div>
            `;
        }

        // Función para guardar información de la mascota
        savePetInfoBtn.addEventListener('click', function() {
            const nombre = petNameInput.value.trim();
            const tipo = petTypeInput.value.trim();
            const cumpleanos = petBirthdayInput.value.trim();
            
            if (!nombre || !tipo || !cumpleanos) {
                alert('Por favor, completa todos los campos.');
                return;
            }
            
            // Validar formato de fecha
            const fechaRegex = /^\d{2}\/\d{2}\/\d{4}$/;
            if (!fechaRegex.test(cumpleanos)) {
                alert('Por favor, ingresa la fecha en formato DD/MM/AAAA (ej: 15/04/2018)');
                return;
            }
            
            // Guardar información
            mascotaInfo = {
                nombre,
                tipo,
                cumpleanos,
                edad: calcularEdadMascota(cumpleanos)
            };
            
            // Mostrar mensaje de confirmación
            addMessage('bot', `¡Genial! Mucho gusto en conocer a ${nombre}. 🐾`);
            addMessage('bot', `Ahora puedo recomendarte los mejores postres para tu ${tipo}. ¿Cómo puedo ayudarte hoy? 😊`);
            
            // Mostrar opciones del menú
            menuOptions.style.display = 'grid';
            mostrarMenuPrincipal();
        });

        // Función para limpiar el formulario
        resetFormBtn.addEventListener('click', function() {
            petNameInput.value = '';
            petTypeInput.value = '';
            petBirthdayInput.value = '';
            petNameInput.focus();
        });

        // Función para volver al menú principal
        backToMenuBtn.addEventListener('click', function() {
            mostrarMenuPrincipal();
        });

        // Función para mostrar información de la mascota
        function mostrarInfoMascota() {
            currentView = 'info';
            backToMenuBtn.style.display = 'inline-flex';
            
            let contenido = `
                <h3><i class="fas fa-paw"></i> Información de ${mascotaInfo.nombre}</h3>
                <div class="pet-info-display">
                    <div class="info-row">
                        <div class="info-label">Nombre:</div>
                        <div class="info-value">${mascotaInfo.nombre}</div>
                    </div>
                    <div class="info-row">
                        <div class="info-label">Tipo:</div>
                        <div class="info-value">${mascotaInfo.tipo}</div>
                    </div>
                    <div class="info-row">
                        <div class="info-label">Cumpleaños:</div>
                        <div class="info-value">${mascotaInfo.cumpleanos}</div>
                    </div>
                    <div class="info-row">
                        <div class="info-label">Edad aproximada:</div>
                        <div class="info-value">${mascotaInfo.edad > 0 ? mascotaInfo.edad + ' años' : 'No se pudo calcular'}</div>
                    </div>
            `;
            
            // Mensaje especial según la edad
            if (mascotaInfo.edad <= 2) {
                contenido += `<p><strong>${mascotaInfo.nombre}</strong> es joven, perfecto para nuestros postres de crecimiento. 🐶</p>`;
            } else if (mascotaInfo.edad <= 7) {
                contenido += `<p><strong>${mascotaInfo.nombre}</strong> está en su mejor edad, ideal para nuestros postres nutritivos. 🐕</p>`;
            } else if (mascotaInfo.edad > 7) {
                contenido += `<p><strong>${mascotaInfo.nombre}</strong> es un veterano, recomendamos postres suaves y fáciles de digerir. 🐾</p>`;
            }
            
            // Verificar si es el mes de cumpleaños
            const hoy = new Date();
            const mesActual = hoy.getMonth() + 1;
            const parts = mascotaInfo.cumpleanos.split('/');
            if (parts.length === 3) {
                const mesCumple = parseInt(parts[1]);
                if (mesCumple === mesActual) {
                    contenido += `<p style="color: #5F82A2; font-weight: 600; margin-top: 15px;">
                        <i class="fas fa-birthday-cake"></i> ¡Este mes es el cumpleaños de ${mascotaInfo.nombre}! 
                        Te recomendamos nuestro <strong>YAKY CELEBRATION CAKE</strong> (Postre #50) para festejar. 🎂
                    </p>`;
                }
            }
            
            contenido += `</div>`;
            resultsContent.innerHTML = contenido;
        }

        // Función para mostrar recomendaciones
        function mostrarRecomendaciones() {
            currentView = 'recommendations';
            backToMenuBtn.style.display = 'inline-flex';
            
            addMessage('bot', `Buscando recomendaciones especiales para ${mascotaInfo.nombre}... 🐾`);
            
            let recomendaciones = [];
            const tipoLower = mascotaInfo.tipo.toLowerCase();
            
            // Filtrar postres según el tipo de mascota (exactamente como en C++)
            if (tipoLower.includes('perro')) {
                recomendaciones = postres.filter(postre => {
                    const saborLower = postre.sabor.toLowerCase();
                    return saborLower.includes('pollo') || 
                           saborLower.includes('zanahoria') ||
                           saborLower.includes('manzana') ||
                           saborLower.includes('avena');
                });
            } else if (tipoLower.includes('gato')) {
                recomendaciones = postres.filter(postre => {
                    const saborLower = postre.sabor.toLowerCase();
                    return saborLower.includes('pollo') || 
                           saborLower.includes('yogurt') ||
                           saborLower.includes('pescado');
                });
            } else {
                // Para otros tipos de mascotas, mostrar los primeros 5 postres
                recomendaciones = postres.slice(0, 5);
            }
            
            // Limitar a 5 recomendaciones (como en C++)
            recomendaciones = recomendaciones.slice(0, 5);
            
            // Mostrar resultados
            let contenido = `<h3><i class="fas fa-paw"></i> Recomendaciones para ${mascotaInfo.nombre}</h3>`;
            
            if (recomendaciones.length > 0) {
                contenido += `<p>Basándome en que ${mascotaInfo.nombre} es un ${mascotaInfo.tipo}, te recomiendo estos postres:</p>`;
                
                recomendaciones.forEach(postre => {
                    contenido += `
                        <div class="postre-card">
                            <h4><i class="fas fa-bone"></i> ${postre.nombre}</h4>
                            <p><strong>Tipo:</strong> ${postre.tipo}</p>
                            <p><strong>Sabor:</strong> ${postre.sabor}</p>
                            <p><strong>ID:</strong> ${postre.id}</p>
                        </div>
                    `;
                });
            } else {
                contenido += `<p>No encontré recomendaciones específicas para ${mascotaInfo.tipo}s. Aquí hay algunos postres populares:</p>`;
                postres.slice(0, 3).forEach(postre => {
                    contenido += `
                        <div class="postre-card">
                            <h4><i class="fas fa-bone"></i> ${postre.nombre}</h4>
                            <p><strong>Tipo:</strong> ${postre.tipo}</p>
                            <p><strong>Sabor:</strong> ${postre.sabor}</p>
                        </div>
                    `;
                });
            }
            
            contenido += `
                <div class="navigation-buttons">
                    <button class="btn btn-secondary" onclick="mostrarMenuPrincipal()">
                        <i class="fas fa-home"></i> Volver al menú
                    </button>
                </div>
            `;
            
            resultsContent.innerHTML = contenido;
        }

        // Función para buscar por tipo
        function buscarPorTipo() {
            currentView = 'search';
            backToMenuBtn.style.display = 'inline-flex';
            
            addMessage('bot', `¿Qué tipo de postre te gustaría buscar? Puedes escribir: CUPCAKE, DONA, GALLETA, HELADO, etc. 🔍`);
            
            // Crear campo de búsqueda
            resultsContent.innerHTML = `
                <h3><i class="fas fa-search"></i> Buscar por tipo de postre</h3>
                <p>Tipos disponibles: CUPCAKE, DONA, GALLETA, HELADO, MUFFIN, PASTEL, BROWNIE, etc.</p>
                <div style="margin: 20px 0;">
                    <input type="text" id="searchType" placeholder="Escribe el tipo de postre..." style="width: 100%;">
                    <button id="searchBtn" class="btn" style="margin-top: 10px;">
                        <i class="fas fa-search"></i> Buscar entre 50 postres
                    </button>
                </div>
                <div id="searchResults"></div>
                <div class="navigation-buttons">
                    <button class="btn btn-secondary" onclick="mostrarMenuPrincipal()">
                        <i class="fas fa-home"></i> Volver al menú
                    </button>
                </div>
            `;
            
            // Configurar evento de búsqueda
            document.getElementById('searchBtn').addEventListener('click', function() {
                const tipoBuscado = document.getElementById('searchType').value.trim().toUpperCase();
                if (!tipoBuscado) {
                    alert('Por favor, escribe un tipo de postre para buscar.');
                    return;
                }
                
                const resultados = postres.filter(postre => 
                    postre.tipo.toUpperCase().includes(tipoBuscado)
                );
                
                let resultadosHTML = '';
                
                if (resultados.length > 0) {
                    resultadosHTML = `<h4>Resultados para "${tipoBuscado}": (${resultados.length} encontrados)</h4>`;
                    resultados.forEach(postre => {
                        resultadosHTML += `
                            <div class="postre-card">
                                <h4><i class="fas fa-bone"></i> ${postre.nombre}</h4>
                                <p><strong>Tipo:</strong> ${postre.tipo}</p>
                                <p><strong>Sabor:</strong> ${postre.sabor}</p>
                                <p><strong>ID:</strong> ${postre.id}</p>
                            </div>
                        `;
                    });
                } else {
                    resultadosHTML = `<p>No se encontraron postres del tipo "${tipoBuscado}". Mostrando algunos postres populares:</p>`;
                    postres.slice(0, 5).forEach(postre => {
                        resultadosHTML += `
                            <div class="postre-card">
                                <h4><i class="fas fa-bone"></i> ${postre.nombre}</h4>
                                <p><strong>Tipo:</strong> ${postre.tipo}</p>
                                <p><strong>Sabor:</strong> ${postre.sabor}</p>
                            </div>
                        `;
                    });
                }
                
                document.getElementById('searchResults').innerHTML = resultadosHTML;
                addMessage('user', `Buscar: ${tipoBuscado}`);
                addMessage('bot', `Encontré ${resultados.length} postres del tipo "${tipoBuscado}" entre nuestros 50 productos. 🐾`);
            });
            
            // Permitir buscar con Enter
            document.getElementById('searchType').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    document.getElementById('searchBtn').click();
                }
            });
        }

        // Función para mostrar todos los postres
        function mostrarTodosPostres() {
            currentView = 'all';
            backToMenuBtn.style.display = 'inline-flex';
            
            addMessage('bot', `Mostrando todos nuestros 50 postres disponibles... 🍰`);
            
            let contenido = `<h3><i class="fas fa-list"></i> Todos nuestros postres para mascotas</h3>`;
            contenido += `<p>Tenemos <strong>${postres.length} postres</strong> disponibles:</p>`;
            
            // Agrupar por tipo para mejor organización
            const postresPorTipo = {};
            postres.forEach(postre => {
                if (!postresPorTipo[postre.tipo]) {
                    postresPorTipo[postre.tipo] = [];
                }
                postresPorTipo[postre.tipo].push(postre);
            });
            
            // Mostrar por tipo
            for (const tipo in postresPorTipo) {
                contenido += `<h4 style="margin-top: 20px; color: #5F82A2; border-bottom: 2px solid #5F82A2; padding-bottom: 5px;">
                    <i class="fas fa-utensils"></i> ${tipo} <span class="counter-badge">${postresPorTipo[tipo].length}</span>
                </h4>`;
                
                postresPorTipo[tipo].forEach(postre => {
                    contenido += `
                        <div class="postre-card">
                            <h4><i class="fas fa-bone"></i> ${postre.nombre}</h4>
                            <p><strong>Tipo:</strong> ${postre.tipo}</p>
                            <p><strong>Sabor:</strong> ${postre.sabor}</p>
                            <p><strong>ID:</strong> ${postre.id}</p>
                        </div>
                    `;
                });
            }
            
            contenido += `
                <div class="navigation-buttons">
                    <button class="btn" onclick="mostrarMenuPrincipal()">
                        <i class="fas fa-home"></i> Volver al menú
                    </button>
                    <button class="btn btn-secondary" onclick="window.scrollTo(0, 0)">
                        <i class="fas fa-arrow-up"></i> Volver arriba
                    </button>
                </div>
            `;
            
            resultsContent.innerHTML = contenido;
        }

        // Función para salir del sistema
        function salirDelSistema() {
            currentView = 'exit';
            backToMenuBtn.style.display = 'none';
            
            addMessage('bot', `Gracias por visitar Nueve Patitas. 😊`);
            addMessage('bot', `Espero que ${mascotaInfo.nombre} disfrute de nuestros 50 postres. ¡Hasta pronto! 🐾`);
            
            resultsContent.innerHTML = `
                <h3><i class="fas fa-sign-out-alt"></i> Sesión finalizada</h3>
                <div class="pet-info-display">
                    <p>Gracias por usar el chatbot Mione. ¡Esperamos verte pronto!</p>
                    <p>Recuerda que ${mascotaInfo.nombre} merece los mejores postres de nuestros 50 productos disponibles. 🐕</p>
                    <p>Si deseas comenzar una nueva sesión, recarga la página.</p>
                </div>
            `;
            
            // Ocultar el menú de opciones
            menuOptions.style.display = 'none';
        }

        // Función para seleccionar una opción del menú
        function seleccionarOpcion(opcion) {
            switch(opcion) {
                case 1:
                    addMessage('user', 'Ver recomendaciones personalizadas');
                    mostrarRecomendaciones();
                    break;
                case 2:
                    addMessage('user', 'Buscar postres por tipo');
                    buscarPorTipo();
                    break;
                case 3:
                    addMessage('user', 'Ver todos los postres');
                    mostrarTodosPostres();
                    break;
                case 4:
                    addMessage('user', 'Ver información de mi mascota');
                    mostrarInfoMascota();
                    break;
                case 5:
                    addMessage('user', 'Salir del sistema');
                    salirDelSistema();
                    break;
            }
        }

        // Configurar eventos de las opciones del menú
        document.getElementById('option1').addEventListener('click', () => seleccionarOpcion(1));
        document.getElementById('option2').addEventListener('click', () => seleccionarOpcion(2));
        document.getElementById('option3').addEventListener('click', () => seleccionarOpcion(3));
        document.getElementById('option4').addEventListener('click', () => seleccionarOpcion(4));
        document.getElementById('option5').addEventListener('click', () => seleccionarOpcion(5));

        // Permitir presionar Enter en el campo de cumpleaños para guardar
        petBirthdayInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                savePetInfoBtn.click();
            }
        });

        // Mensaje inicial
        addMessage('bot', '¡Bienvenido a Nueve Patitas! 🐾<br>Mi nombre es Mione y estaré encantada de ayudarte a encontrar los mejores postres para tu mascota. 😊<br><br>Por favor, completa la información de tu mascota para comenzar.');
    </script>
</body>
</html>
