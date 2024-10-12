<body>
    <h1>Calculadora de Huella de Carbono</h1>

    <form id="carbonForm">
        <label for="envases">Cantidad de envases reciclables/biodegradables usados por mes:</label>
        <input type="number" id="envases" name="envases" min="0" step="1" required><br><br>

        <label for="frutas">Kilos de frutas comprados semanalmente:</label>
        <input type="number" id="frutas" name="frutas" min="0" step="0.1" required><br><br>

        <label for="compostaje">Kilos de residuos de frutas compostados por mes:</label>
        <input type="number" id="compostaje" name="compostaje" min="0" step="0.1" required><br><br>

        <label for="clientes">Número de clientes que traen sus propios envases por mes:</label>
        <input type="number" id="clientes" name="clientes" min="0" step="1" required><br><br>

        <button type="submit">Calcular Huella de Carbono</button>
    </form>

    <h2>Resultado:</h2>
    <p id="resultado">La huella de carbono estimada será mostrada aquí.</p>

    <script>
        document.getElementById("carbonForm").addEventListener("submit", function(event) {
            event.preventDefault();

            // Datos de entrada del usuario
            const envases = parseInt(document.getElementById("envases").value);
            const frutas = parseFloat(document.getElementById("frutas").value);
            const compostaje = parseFloat(document.getElementById("compostaje").value);
            const clientes = parseInt(document.getElementById("clientes").value);

            // Factores estimados de huella de carbono (pueden ajustarse según la realidad local)
            const factorEnvases = 0.02; // kg CO2 por envase reciclable
            const factorFrutas = 0.1;   // kg CO2 por kg de fruta desperdiciada
            const factorCompostaje = -0.05; // kg CO2 ahorrado por kg de compostaje
            const factorClientes = -0.01;   // kg CO2 ahorrado por cliente que trae su envase

            // Cálculo de huella de carbono
            let huellaCarbono = 0;
            huellaCarbono += envases * factorEnvases;
            huellaCarbono += frutas * 4 * factorFrutas; // 4 semanas en un mes
            huellaCarbono += compostaje * factorCompostaje;
            huellaCarbono += clientes * factorClientes;

            // Mostrar el resultado
            document.getElementById("resultado").textContent = "La huella de carbono estimada es: " + huellaCarbono.toFixed(2) + " kg CO2 por mes.";
        });
    </script>
</body>
