# SuraCa
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GRUPO SURA</title>
    <style>
        /* Estilos básicos */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f8ff; /* Celeste claro */
            color: #333;
        }
        header {
            background-color: white;
            padding: 20px;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        header h1 {
            color: #007acc;
            font-size: 2.5em;
        }
        .menu {
            display: flex;
            justify-content: center;
            margin: 20px;
        }
        .menu button {
            background-color: #007acc;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            margin: 0 10px;
            cursor: pointer;
            font-size: 1.2em;
        }
        .menu button:hover {
            background-color: #005f99;
        }
        .form-section {
            display: none;
            margin: 20px;
            padding: 20px;
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            border-radius: 5px;
        }
        form input, form select {
            margin: 10px 0;
            padding: 10px;
            width: 100%;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .submit-btn {
            background-color: #007acc;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .submit-btn:hover {
            background-color: #005f99;
        }
    </style>
</head>
<body>
    <header>
        <h1>CA Sura</h1>
        <p>Nuestro mejor activo: la gente</p>
    </header>

    <div class="menu">
        <button onclick="showSection('seguros')">Seguros</button>
        <button onclick="showSection('trabajos')">Ofertas de Trabajo</button>
        <button onclick="showSection('citas')">Citas Médicas</button>
    </div>

    <!-- Sección de Seguros -->
    <div id="seguros" class="form-section">
        <h2>Seguros</h2>
        <form id="segurosForm">
            <select name="tipo" required>
                <option value="" disabled selected>Tipo de Seguro</option>
                <option value="Médico">Médico</option>
                <option value="Propiedades">Propiedades</option>
            </select>
            <input type="text" name="user" placeholder="Usuario" required>
            <input type="text" name="nombre" placeholder="Nombre y Apellidos" required>
            <input type="text" name="sujeto" placeholder="Sujeto del Seguro" required>
            <input type="number" name="duracion" placeholder="Duración (meses)" required>
            <button type="submit" class="submit-btn">Enviar</button>
        </form>
    </div>

    <!-- Sección de Trabajos -->
    <div id="trabajos" class="form-section">
        <h2>Ofertas de Trabajo</h2>
        <form id="trabajosForm">
            <select name="puesto" required>
                <option value="" disabled selected>Selecciona un Puesto</option>
                <option value="Paramédico">Paramédico</option>
                <option value="Enfermería">Enfermería</option>
                <option value="Médico">Médico</option>
                <option value="Cirujano">Cirujano</option>
            </select>
            <input type="text" name="user" placeholder="Usuario" required>
            <input type="text" name="nombre" placeholder="Nombre y Apellidos" required>
            <input type="number" name="edad" placeholder="Edad" required>
            <input type="text" name="experiencias" placeholder="Experiencias" required>
            <button type="submit" class="submit-btn">Enviar</button>
        </form>
    </div>

    <!-- Sección de Citas Médicas -->
    <div id="citas" class="form-section">
        <h2>Citas Médicas</h2>
        <form id="citasForm">
            <input type="text" name="user" placeholder="Usuario" required>
            <input type="text" name="nombre" placeholder="Nombre y Apellidos" required>
            <input type="number" name="edad" placeholder="Edad" required>
            <input type="text" name="consulta" placeholder="Tipo de Consulta" required>
            <input type="datetime-local" name="fecha" required>
            <button type="submit" class="submit-btn">Enviar</button>
        </form>
    </div>

    <script>
        function showSection(sectionId) {
            const sections = document.querySelectorAll('.form-section');
            sections.forEach(section => section.style.display = 'none');
            document.getElementById(sectionId).style.display = 'block';
        }

        // Ejemplo para enviar un formulario al webhook de Discord
        const webhookUrl = "TU_WEBHOOK_URL"; // Reemplaza con la URL del webhook

        document.querySelectorAll('form').forEach(form => {
            form.addEventListener('submit', e => {
                e.preventDefault();
                const formData = new FormData(form);
                const data = {};
                formData.forEach((value, key) => data[key] = value);

                fetch(webhookUrl, {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify({ content: JSON.stringify(data) })
                })
                .then(() => alert('Formulario enviado correctamente.'))
                .catch(() => alert('Error al enviar.'));
            });
        });
    </script>
    <div class="creator">
        <img src="https://postimg.cc/KkZ9NjZt" alt="Creador">
        <p>CREADOR: JJ26M</p>
    </div>
</body>
</html>
