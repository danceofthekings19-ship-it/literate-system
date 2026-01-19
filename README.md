# literate-system
Calculadora de varianza muestral y poblacional
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora Poblacional y Muestral</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            padding: 30px;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            border-bottom: 2px solid #4a6fa5;
            padding-bottom: 20px;
        }
        
        h1 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #7f8c8d;
            font-size: 1.1rem;
        }
        
        .app-description {
            background-color: #e8f4fc;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 25px;
            border-left: 4px solid #3498db;
        }
        
        .calculator-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        @media (max-width: 768px) {
            .calculator-container {
                grid-template-columns: 1fr;
            }
        }
        
        .section {
            background-color: #f9f9f9;
            padding: 20px;
            border-radius: 8px;
            border: 1px solid #e0e0e0;
        }
        
        .section h2 {
            color: #2c3e50;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #ddd;
            display: flex;
            align-items: center;
        }
        
        .section h2 i {
            margin-right: 10px;
            color: #3498db;
        }
        
        .input-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #2c3e50;
        }
        
        input, select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        
        input:focus, select:focus {
            outline: none;
            border-color: #3498db;
        }
        
        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: background-color 0.3s;
            width: 100%;
            margin-top: 10px;
        }
        
        button:hover {
            background-color: #2980b9;
        }
        
        .btn-calculate {
            background-color: #2ecc71;
        }
        
        .btn-calculate:hover {
            background-color: #27ae60;
        }
        
        .results {
            margin-top: 25px;
            background-color: #e8f4fc;
            padding: 20px;
            border-radius: 8px;
            border-left: 4px solid #3498db;
        }
        
        .results h3 {
            color: #2c3e50;
            margin-bottom: 15px;
        }
        
        .result-item {
            display: flex;
            justify-content: space-between;
            padding: 10px 0;
            border-bottom: 1px solid #d1e7f5;
        }
        
        .result-item:last-child {
            border-bottom: none;
        }
        
        .result-label {
            font-weight: 600;
            color: #2c3e50;
        }
        
        .result-value {
            font-weight: 600;
            color: #3498db;
        }
        
        .formula {
            font-style: italic;
            color: #7f8c8d;
            font-size: 0.9rem;
            margin-top: 5px;
        }
        
        .footer {
            text-align: center;
            margin-top: 30px;
            color: #7f8c8d;
            font-size: 0.9rem;
            border-top: 1px solid #eee;
            padding-top: 20px;
        }
        
        .instructions {
            background-color: #fff8e1;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            border-left: 4px solid #f39c12;
        }
        
        .instructions h3 {
            color: #e67e22;
            margin-bottom: 10px;
        }
        
        .instructions ul {
            padding-left: 20px;
        }
        
        .instructions li {
            margin-bottom: 8px;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Calculadora Poblacional y Muestral</h1>
            <p class="subtitle">Herramienta para cálculos estadísticos de población y muestra</p>
        </header>
        
        <div class="app-description">
            <p>Esta calculadora permite realizar cálculos estadísticos para poblaciones completas y muestras. Introduce tus datos en la sección correspondiente y obtén resultados instantáneos.</p>
        </div>
        
        <div class="calculator-container">
            <div class="section">
                <h2><i>📊</i> Calculadora Poblacional</h2>
                <p>Introduce los datos de toda la población para calcular estadísticos poblacionales.</p>
                
                <div class="input-group">
                    <label for="population-data">Datos poblacionales (separados por comas):</label>
                    <input type="text" id="population-data" placeholder="Ejemplo: 12, 15, 18, 20, 22, 25, 28, 30">
                    <p class="formula">Media poblacional: μ = Σx / N</p>
                    <p class="formula">Varianza poblacional: σ² = Σ(x - μ)² / N</p>
                </div>
                
                <button class="btn-calculate" onclick="calculatePopulation()">Calcular Estadísticos Poblacionales</button>
                
                <div class="results" id="population-results" style="display: none;">
                    <h3>Resultados Poblacionales</h3>
                    <div class="result-item">
                        <span class="result-label">Tamaño de población (N):</span>
                        <span class="result-value" id="pop-size">0</span>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Media poblacional (μ):</span>
                        <span class="result-value" id="pop-mean">0</span>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Varianza poblacional (σ²):</span>
                        <span class="result-value" id="pop-variance">0</span>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Desviación estándar (σ):</span>
                        <span class="result-value" id="pop-stddev">0</span>
                    </div>
                </div>
            </div>
            
            <div class="section">
                <h2><i>🔬</i> Calculadora Muestral</h2>
                <p>Introduce los datos de una muestra para calcular estadísticos muestrales.</p>
                
                <div class="input-group">
                    <label for="sample-data">Datos de la muestra (separados por comas):</label>
                    <input type="text" id="sample-data" placeholder="Ejemplo: 15, 18, 22, 25, 28">
                    <p class="formula">Media muestral: x̄ = Σx / n</p>
                    <p class="formula">Varianza muestral: s² = Σ(x - x̄)² / (n-1)</p>
                </div>
                
                <button class="btn-calculate" onclick="calculateSample()">Calcular Estadísticos Muestrales</button>
                
                <div class="results" id="sample-results" style="display: none;">
                    <h3>Resultados Muestrales</h3>
                    <div class="result-item">
                        <span class="result-label">Tamaño de muestra (n):</span>
                        <span class="result-value" id="sample-size">0</span>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Media muestral (x̄):</span>
                        <span class="result-value" id="sample-mean">0</span>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Varianza muestral (s²):</span>
                        <span class="result-value" id="sample-variance">0</span>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Desviación estándar (s):</span>
                        <span class="result-value" id="sample-stddev">0</span>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="section">
            <h2><i>📐</i> Cálculo de Tamaño de Muestra</h2>
            <p>Calcula el tamaño de muestra necesario para un estudio basado en parámetros poblacionales.</p>
            
            <div class="input-group">
                <label for="population-size">Tamaño de la población (N):</label>
                <input type="number" id="population-size" placeholder="Ejemplo: 1000" min="1">
            </div>
            
            <div class="input-group">
                <label for="confidence-level">Nivel de confianza:</label>
                <select id="confidence-level">
                    <option value="1.96">95% (Z = 1.96)</option>
                    <option value="2.576">99% (Z = 2.576)</option>
                    <option value="1.645">90% (Z = 1.645)</option>
                    <option value="2.326">98% (Z = 2.326)</option>
                </select>
            </div>
            
            <div class="input-group">
                <label for="margin-error">Margen de error (E):</label>
                <input type="number" id="margin-error" placeholder="Ejemplo: 0.05 (5%)" step="0.01" min="0.01" max="1">
            </div>
            
            <div class="input-group">
                <label for="proportion">Proporción esperada (p):</label>
                <input type="number" id="proportion" placeholder="Ejemplo: 0.5 (50%)" step="0.01" min="0.01" max="0.99" value="0.5">
                <p class="formula">Fórmula: n = N * Z² * p * (1-p) / [E² * (N-1) + Z² * p * (1-p)]</p>
            </div>
            
            <button class="btn-calculate" onclick="calculateSampleSize()">Calcular Tamaño de Muestra</button>
            
            <div class="results" id="sample-size-results" style="display: none;">
                <h3>Resultados del Tamaño de Muestra</h3>
                <div class="result-item">
                    <span class="result-label">Tamaño de muestra necesario:</span>
                    <span class="result-value" id="required-sample-size">0</span>
                </div>
                <div class="result-item">
                    <span class="result-label">Tamaño de población:</span>
                    <span class="result-value" id="input-population-size">0</span>
                </div>
                <div class="result-item">
                    <span class="result-label">Nivel de confianza:</span>
                    <span class="result-value" id="input-confidence">0</span>
                </div>
                <div class="result-item">
                    <span class="result-label">Margen de error:</span>
                    <span class="result-value" id="input-margin">0</span>
                </div>
            </div>
        </div>
        
        <div class="instructions">
            <h3>Instrucciones de uso</h3>
            <ul>
                <li><strong>Calculadora poblacional:</strong> Introduce todos los valores de la población separados por comas para obtener la media, varianza y desviación estándar poblacionales.</li>
                <li><strong>Calculadora muestral:</strong> Introduce los valores de una muestra separados por comas para obtener estadísticos muestrales.</li>
                <li><strong>Cálculo de tamaño de muestra:</strong> Especifica los parámetros de tu estudio para determinar el tamaño de muestra necesario.</li>
                <li>Los resultados se redondean a 4 decimales para mayor claridad.</li>
            </ul>
        </div>
        
        <div class="footer">
            <p>Calculadora Estadística - Herramienta educativa para análisis poblacional y muestral</p>
            <p>© 2023 - Diseñado para fines educativos</p>
        </div>
    </div>

    <script>
        // Función para convertir texto a array de números
        function parseData(input) {
            // Eliminar espacios y dividir por comas
            const values = input.split(',');
            const numbers = [];
            
            for (let value of values) {
                // Eliminar espacios en blanco y convertir a número
                const num = parseFloat(value.trim());
                
                // Verificar que es un número válido
                if (!isNaN(num)) {
                    numbers.push(num);
                }
            }
            
            return numbers;
        }
        
        // Calcular media (promedio)
        function calculateMean(data) {
            if (data.length === 0) return 0;
            
            const sum = data.reduce((acc, val) => acc + val, 0);
            return sum / data.length;
        }
        
        // Calcular varianza poblacional
        function calculatePopulationVariance(data, mean) {
            if (data.length === 0) return 0;
            
            const squaredDifferences = data.map(val => Math.pow(val - mean, 2));
            const sumSquaredDiff = squaredDifferences.reduce((acc, val) => acc + val, 0);
            
            return sumSquaredDiff / data.length;
        }
        
        // Calcular varianza muestral
        function calculateSampleVariance(data, mean) {
            if (data.length <= 1) return 0;
            
            const squaredDifferences = data.map(val => Math.pow(val - mean, 2));
            const sumSquaredDiff = squaredDifferences.reduce((acc, val) => acc + val, 0);
            
            return sumSquaredDiff / (data.length - 1);
        }
        
        // Calcular desviación estándar (raíz cuadrada de la varianza)
        function calculateStdDev(variance) {
            return Math.sqrt(variance);
        }
        
        // Formatear número a 4 decimales
        function formatNumber(num) {
            return Number(num.toFixed(4));
        }
        
        // Calcular estadísticos poblacionales
        function calculatePopulation() {
            const input = document.getElementById('population-data').value;
            const data = parseData(input);
            
            if (data.length === 0) {
                alert('Por favor, introduce datos válidos separados por comas.');
                return;
            }
            
            const mean = calculateMean(data);
            const variance = calculatePopulationVariance(data, mean);
            const stdDev = calculateStdDev(variance);
            
            // Mostrar resultados
            document.getElementById('pop-size').textContent = data.length;
            document.getElementById('pop-mean').textContent = formatNumber(mean);
            document.getElementById('pop-variance').textContent = formatNumber(variance);
            document.getElementById('pop-stddev').textContent = formatNumber(stdDev);
            
            // Mostrar sección de resultados
            document.getElementById('population-results').style.display = 'block';
        }
        
        // Calcular estadísticos muestrales
        function calculateSample() {
            const input = document.getElementById('sample-data').value;
            const data = parseData(input);
            
            if (data.length === 0) {
                alert('Por favor, introduce datos válidos separados por comas.');
                return;
            }
            
            if (data.length === 1) {
                alert('Para calcular varianza muestral se necesitan al menos 2 datos.');
                return;
            }
            
            const mean = calculateMean(data);
            const variance = calculateSampleVariance(data, mean);
            const stdDev = calculateStdDev(variance);
            
            // Mostrar resultados
            document.getElementById('sample-size').textContent = data.length;
            document.getElementById('sample-mean').textContent = formatNumber(mean);
            document.getElementById('sample-variance').textContent = formatNumber(variance);
            document.getElementById('sample-stddev').textContent = formatNumber(stdDev);
            
            // Mostrar sección de resultados
            document.getElementById('sample-results').style.display = 'block';
        }
        
        // Calcular tamaño de muestra necesario
        function calculateSampleSize() {
            const populationSize = parseInt(document.getElementById('population-size').value);
            const confidenceLevel = parseFloat(document.getElementById('confidence-level').value);
            const marginError = parseFloat(document.getElementById('margin-error').value);
            const proportion = parseFloat(document.getElementById('proportion').value);
            
            // Validar entradas
            if (isNaN(populationSize) || populationSize <= 0) {
                alert('Por favor, introduce un tamaño de población válido.');
                return;
            }
            
            if (isNaN(marginError) || marginError <= 0 || marginError >= 1) {
                alert('Por favor, introduce un margen de error válido (entre 0 y 1).');
                return;
            }
            
            if (isNaN(proportion) || proportion <= 0 || proportion >= 1) {
                alert('Por favor, introduce una proporción válida (entre 0 y 1).');
                return;
            }
            
            // Calcular tamaño de muestra usando la fórmula para poblaciones finitas
            const zSquared = Math.pow(confidenceLevel, 2);
            const pTimesQ = proportion * (1 - proportion);
            const eSquared = Math.pow(marginError, 2);
            
            // Fórmula para población finita
            const numerator = populationSize * zSquared * pTimesQ;
            const denominator = eSquared * (populationSize - 1) + zSquared * pTimesQ;
            
            let sampleSize = Math.ceil(numerator / denominator);
            
            // Asegurar que el tamaño de muestra no sea mayor que la población
            if (sampleSize > populationSize) {
                sampleSize = populationSize;
            }
            
            // Mostrar resultados
            document.getElementById('required-sample-size').textContent = sampleSize;
            document.getElementById('input-population-size').textContent = populationSize;
            document.getElementById('input-confidence').textContent = document.getElementById('confidence-level').options[document.getElementById('confidence-level').selectedIndex].text;
            document.getElementById('input-margin').textContent = marginError;
            
            // Mostrar sección de resultados
            document.getElementById('sample-size-results').style.display = 'block';
        }
        
        // Ejemplos precargados para facilitar las pruebas
        window.onload = function() {
            // Precargar ejemplos
            document.getElementById('population-data').value = "12, 15, 18, 20, 22, 25, 28, 30";
            document.getElementById('sample-data').value = "15, 18, 22, 25, 28";
            document.getElementById('population-size').value = "1000";
            document.getElementById('margin-error').value = "0.05";
        };
    </script>
</body>
</html>
