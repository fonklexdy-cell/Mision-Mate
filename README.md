
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Misiòn Mates</title>
    <style>
        :root {
            --amarillo: #FFD166;
            --azul: #118AB2;
            --verde: #06D6A0;
            --naranja: #F77F00;
            --rosa: #EF476F;
            --oscuro: #073B4C;
            --blanco: #FFFFFF;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, var(--azul), var(--oscuro));
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: var(--oscuro);
            padding: 15px;
        }

        .contenedor-juego {
            background-color: var(--blanco);
            width: 100%;
            max-width: 600px;
            border-radius: 24px;
            box-shadow: 0 12px 30px rgba(0,0,0,0.3);
            overflow: hidden;
            text-align: center;
            padding: 25px;
            transition: all 0.3s ease;
        }

        /* Pantallas */
        .pantalla {
            display: none;
        }

        .pantalla.activa {
            display: flex;
            flex-direction: column;
            gap: 20px;
            align-items: center;
        }

        /* Títulos y Textos */
        h1 {
            color: var(--naranja);
            font-size: 2.2rem;
            text-shadow: 2px 2px var(--amarillo);
            margin-bottom: 10px;
        }

        p {
            font-size: 1.1rem;
            color: var(--oscuro);
            font-weight: 500;
        }

        /* Componentes Interactivos */
        .marcador-contenedor {
            display: flex;
            justify-content: space-between;
            width: 100%;
            background-color: #f0f4f8;
            padding: 10px 20px;
            border-radius: 50px;
            font-weight: bold;
            font-size: 1.1rem;
        }

        .tiempo-alerta {
            color: var(--rosa);
            animation: pulso 0.5s infinite alternate;
        }

        /* Área de Desafío */
        .avatar-contenedor {
            width: 140px;
            height: 140px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 5rem;
            background-color: var(--amarillo);
            border: 5px solid var(--blanco);
            box-shadow: 0 6px 15px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }

        .burbuja-texto {
            background-color: #f0f4f8;
            padding: 12px 20px;
            border-radius: 15px;
            font-weight: bold;
            max-width: 90%;
            border: 2px solid #ddd;
            min-height: 48px;
        }

        .operacion-imagen {
            font-size: 3.5rem;
            font-weight: 800;
            padding: 15px 30px;
            border-radius: 20px;
            background-color: #f8f9fa;
            border-bottom: 5px solid #ddd;
            width: 100%;
            letter-spacing: 2px;
        }

        /* Opciones de Respuesta */
        .opciones-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            width: 100%;
        }

        /* Botones */
        .btn {
            background-color: var(--azul);
            color: var(--blanco);
            border: none;
            padding: 15px 25px;
            font-size: 1.2rem;
            font-weight: bold;
            border-radius: 15px;
            cursor: pointer;
            transition: transform 0.1s, background-color 0.2s;
            box-shadow: 0 4px 0px rgba(0,0,0,0.15);
            width: 100%;
        }

        .btn:active {
            transform: translateY(4px);
            box-shadow: none;
        }

        .btn-inicio { background-color: var(--verde); font-size: 1.4rem; padding: 18px; }
        .btn-reinicio { background-color: var(--rosa); }
        
        /* Colores del grid de respuestas */
        .opciones-grid .btn:nth-child(1) { background-color: var(--azul); }
        .opciones-grid .btn:nth-child(2) { background-color: var(--naranja); }
        .opciones-grid .btn:nth-child(3) { background-color: var(--rosa); }
        .opciones-grid .btn:nth-child(4) { background-color: var(--verde); }

        /* Pantalla Final */
        .medalla {
            font-size: 6rem;
            animation: flotar 2s ease-in-out infinite;
        }

        .tabla-resultados {
            width: 100%;
            margin: 15px 0;
            border-collapse: collapse;
        }

        .tabla-resultados th, .tabla-resultados td {
            padding: 10px;
            border-bottom: 1px solid #ddd;
        }

        /* Animaciones */
        @keyframes pulso {
            from { transform: scale(1); }
            to { transform: scale(1.05); }
        }

        @keyframes flotar {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }

        /* Responsividad */
        @media (max-width: 480px) {
            h1 { font-size: 1.8rem; }
            .operacion-imagen { font-size: 2.5rem; }
            .opciones-grid { grid-template-columns: 1fr; }
            .avatar-contenedor { width: 110px; height: 110px; font-size: 4rem; }
            .contenedor-juego { padding: 15px; }
        }
        .btn-flotante-mateken {
    position: fixed;
    bottom: 25px;
    right: 25px;
    background-color: #FFD166;
    color: #073B4C;
    padding: 15px 22px;
    font-size: 1.1rem;
    font-weight: bold;
    text-decoration: none;
    border-radius: 50px;
    box-shadow: 0 6px 15px rgba(0,0,0,0.4);
    display: flex;
    align-items: center;
    gap: 10px;
    transition: transform 0.2s, background-color 0.2s;
    z-index: 9999;
    font-family: sans-serif;
}
.btn-flotante-mateken:hover {
    transform: scale(1.1);
    background-color: #fffde7;
}
    </style>
</head>
<body>

    <div class="contenedor-juego">
        
        <!-- PANTALLA INICIO -->
        <div id="pantalla-inicio" class="pantalla activa">
            <h1>Misiòn Mate</h1>
            <p>¡Supera el laberinto resolviendo las operaciones fundamentales! Las respuestas correctas suman y los errores restan puntaje.</p>
            <div style="font-size: 5rem; margin: 15px 0;">🧠⚡🧮</div>
            <button class="btn btn-inicio" onclick="iniciarJuego()">¡COMENZAR DESAFÍO!</button>
        </div>

        <!-- PANTALLA JUEGO -->
        <div id="pantalla-juego" class="pantalla">
            <div class="marcador-contenedor">
                <div>Progreso: <span id="ronda-actual">1</span>/12</div>
                <div>Puntos: <span id="puntos">0</span></div>
                <div id="cronometro-box">Tiempo: <span id="tiempo">20</span>s</div>
            </div>

            <div class="avatar-contenedor" id="avatar">🧙‍♂️</div>
            <div class="burbuja-texto" id="burbuja">¡Demuestra tu velocidad matemática!</div>

            <!-- Espacio para la operación matemática e icono de la actividad -->
            <div class="operacion-imagen" id="bloque-operacion">0 + 0</div>

            <div class="opciones-grid" id="contenedor-opciones">
                <!-- Botones inyectados dinámicamente por JavaScript -->
            </div>
        </div>

        <!-- PANTALLA FINAL -->
        <div id="pantalla-final" class="pantalla">
            <h1>Desafío Completado</h1>
            <div class="medalla" id="logro-medalla">🥇</div>
            <h2 id="logro-titulo">¡Maestro Calculador!</h2>
            <p id="logro-descripcion">Has dominado el laberinto a la perfección.</p>
            
            <table class="tabla-resultados">
                <thead>
                    <tr>
                        <th style="text-align: left;">Métrica</th>
                        <th style="text-align: right;">Resultado</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td style="text-align: left;">Preguntas Totales</td>
                        <td style="text-align: right;">12</td>
                    </tr>
                    <tr>
                        <td style="text-align: left;">Respuestas Correctas</td>
                        <td id="res-correctas" style="text-align: right; color: var(--verde); font-weight: bold;">0</td>
                    </tr>
                    <tr>
                        <td style="text-align: left;">Respuestas Incorrectas</td>
                        <td id="res-incorrectas" style="text-align: right; color: var(--rosa); font-weight: bold;">0</td>
                    </tr>
                    <tr>
                        <td style="text-align: left;">Nota o Rendimiento</td>
                        <td id="res-nota" style="text-align: right; font-weight: bold;">0%</td>
                    </tr>
                </tbody>
            </table>

            <button class="btn btn-reinicio" onclick="iniciarJuego()">REINTENTAR (Nuevos Ejercicios)</button>
        </div>

    </div>

    <script>
        // Variables globales del sistema de juego
        let puntosBase = 0;
        let tiempoRestante = 20;
        let temporizador = null;
        let respuestaCorrecta = 0;
        let correctasContadas = 0;
        let incorrectasContadas = 0;
        let totalPreguntas = 0;
        const maxPreguntas = 12; // Modificado exactamente a 12 ejercicios fijos

        // Configuración de Actividades Variadas, Avatares y Colores Contextuales
        const configuracionOperaciones = {
            '+': { emoji: '➕', avatar: '🧙‍♂️', color: 'var(--azul)' },
            '-': { emoji: '➖', avatar: '🥷', color: 'var(--naranja)' },
            '*': { emoji: '✖️', avatar: '🤖', color: 'var(--rosa)' },
            '/': { emoji: '➗', avatar: '🦄', color: 'var(--verde)' }
        };

        // Contexto de Audio Web Nativo para evitar dependencias externas en GitHub
        let ctxAudio = null;

        function inicializarAudio() {
            if (!ctxAudio) {
                ctxAudio = new (window.AudioContext || window.webkitAudioContext)();
            }
        }

        function reproducirSonido(tipo) {
            inicializarAudio();
            if (!ctxAudio) return;

            const osc = ctxAudio.createOscillator();
            const ganancia = ctxAudio.createGain();
            osc.connect(ganancia);
            ganancia.connect(ctxAudio.destination);

            const ahora = ctxAudio.currentTime;

            if (tipo === 'correcto') {
                osc.type = 'triangle';
                osc.frequency.setValueAtTime(523.25, ahora); // Nota Do (C5)
                osc.frequency.setValueAtTime(659.25, ahora + 0.1); // Nota Mi (E5)
                osc.frequency.setValueAtTime(783.99, ahora + 0.2); // Nota Sol (G5)
                ganancia.gain.setValueAtTime(0.3, ahora);
                ganancia.gain.exponentialRampToValueAtTime(0.01, ahora + 0.4);
                osc.start(ahora);
                osc.stop(ahora + 0.4);
            } else if (tipo === 'incorrecto') {
                osc.type = 'sawtooth';
                osc.frequency.setValueAtTime(150, ahora);
                osc.frequency.linearRampToValueAtTime(80, ahora + 0.3);
                ganancia.gain.setValueAtTime(0.4, ahora);
                ganancia.gain.exponentialRampToValueAtTime(0.01, ahora + 0.3);
                osc.start(ahora);
                osc.stop(ahora + 0.3);
            } else if (tipo === 'final') {
                // Acorde envolvente armónico de victoria progresivo
                const notas = [261.63, 329.63, 392.00, 523.25];
                notas.forEach((frec) => {
                    const o = ctxAudio.createOscillator();
                    const g = ctxAudio.createGain();
                    o.connect(g);
                    g.connect(ctxAudio.destination);
                    o.type = 'sine';
                    o.frequency.setValueAtTime(frec, ahora);
                    o.frequency.exponentialRampToValueAtTime(frec * 2, ahora + 1.5);
                    g.gain.setValueAtTime(0.12, ahora);
                    g.gain.exponentialRampToValueAtTime(0.001, ahora + 2);
                    o.start(ahora);
                    o.stop(ahora + 2);
                });
            }
        }

        // Control y navegación de pantallas del juego
        function cambiarPantalla(idPantalla) {
            document.querySelectorAll('.pantalla').forEach(p => p.classList.remove('activa'));
            document.getElementById(idPantalla).classList.add('activa');
        }

        // Inicializador del ciclo principal
        function iniciarJuego() {
            inicializarAudio();
            puntosBase = 0;
            correctasContadas = 0;
            incorrectasContadas = 0;
            totalPreguntas = 0;
            document.getElementById('puntos').innerText = puntosBase;
            cambiarPantalla('pantalla-juego');
            generarNuevaActividad();
        }
        // Generador aleatorio de actividades fundamentales (Tablas 2-12, sumas y restas de 2 cifras)
        function generarNuevaActividad() {
            if (totalPreguntas >= maxPreguntas) {
                finalizarJuego();
                return;
            }

            totalPreguntas++;
            document.getElementById('ronda-actual').innerText = totalPreguntas;
            tiempoRestante = 20;
            document.getElementById('tiempo').innerText = tiempoRestante;
            document.getElementById('cronometro-box').classList.remove('tiempo-alerta');

            // Restablecer mensajes por defecto del avatar
            document.getElementById('burbuja').innerText = "¡Resuelve rápido!";
            document.getElementById('burbuja').style.color = 'var(--oscuro)';

            // Banco de tipos de operaciones fundamentales
            const operaciones = ['+', '-', '*', '/'];
            const op = operaciones[Math.floor(Math.random() * operaciones.length)];
            const conf = configuracionOperaciones[op];

            // Renderizar dinámicamente el avatar asignado a la actividad
            const avatarElem = document.getElementById('avatar');
            avatarElem.innerText = conf.avatar;
            avatarElem.style.backgroundColor = conf.color;

            let num1 = 0;
            let num2 = 0;

            // Motor lógico con las restricciones solicitadas
            if (op === '+') {
                // Sumas de 2 cifras (de 10 a 99)
                num1 = Math.floor(Math.random() * 90) + 10;
                num2 = Math.floor(Math.random() * 90) + 10;
                respuestaCorrecta = num1 + num2;
            } else if (op === '-') {
                // Restas de 2 cifras sin resultados negativos
                num1 = Math.floor(Math.random() * 90) + 10;
                num2 = Math.floor(Math.random() * (num1 - 10)) + 10; 
                respuestaCorrecta = num1 - num2;
            } else if (op === '*') {
                // Multiplicaciones de las tablas del 2 al 12
                num1 = Math.floor(Math.random() * 11) + 2;
                num2 = Math.floor(Math.random() * 11) + 2;
                respuestaCorrecta = num1 * num2;
            } else if (op === '/') {
                // Divisiones exactas basadas en tablas del 2 al 12
                num2 = Math.floor(Math.random() * 11) + 2; // Divisor (2 al 12)
                respuestaCorrecta = Math.floor(Math.random() * 11) + 2; // Cociente (2 al 12)
                num1 = num2 * respuestaCorrecta; // Dividendo exacto de 2 cifras o correspondiente
            }

            // Inyección visual de la actividad
            document.getElementById('bloque-operacion').innerHTML = `${num1} ${conf.emoji} ${num2}`;

            // Algoritmo de generación de opciones falsas (distractores cercanos válidos)
            let opciones = [respuestaCorrecta];
            while (opciones.length < 4) {
                let desvio = respuestaCorrecta + (Math.floor(Math.random() * 14) - 7);
                if (desvio !== respuestaCorrecta && desvio >= 0 && !opciones.includes(desvio)) {
                    opciones.push(desvio);
                }
            }
            
            // Mezclado aleatorio del orden de las respuestas
            opciones.sort(() => Math.random() - 0.5);

            // Renderizar botones en la cuadrícula adaptativa
            const contenedorOpciones = document.getElementById('contenedor-opciones');
            contenedorOpciones.innerHTML = '';
            opciones.forEach(opc => {
                const boton = document.createElement('button');
                boton.className = 'btn';
                boton.innerText = opc;
                boton.onclick = () => verificarRespuesta(opc);
                contenedorOpciones.appendChild(boton);
            });

            // Motor del temporizador por actividad
            if (temporizador) clearInterval(temporizador);
            temporizador = setInterval(() => {
                tiempoRestante--;
                document.getElementById('tiempo').innerText = tiempoRestante;
                
                if (tiempoRestante <= 5) {
                    document.getElementById('cronometro-box').classList.add('tiempo-alerta');
                }

                if (tiempoRestante <= 0) {
                    clearInterval(temporizador);
                    procesarFallo(true);
                }
            }, 1000);
        }

        // Verificación lógica de la respuesta seleccionada
        function verificarRespuesta(seleccionada) {
            if (temporizador) clearInterval(temporizador);
            
            if (seleccionada === respuestaCorrecta) {
                puntosBase += 10; // Suma fija por acierto
                correctasContadas++;
                document.getElementById('puntos').innerText = puntosBase;
                
                reproducirSonido('correcto');
                document.getElementById('burbuja').innerText = "CORRECTO";
                document.getElementById('burbuja').style.color = "var(--verde)";
                
                setTimeout(generarNuevaActividad, 1200);
            } else {
                procesarFallo(false);
            }
        }

        // Procesamiento en caso de error o fin de tiempo (Penaliza restando puntos)
        function procesarFallo(porTiempo) {
            if (temporizador) clearInterval(temporizador);
            incorrectasContadas++;
            
            // Penalización por confusión o tiempo agotado: resta 5 puntos
            puntosBase = Math.max(0, puntosBase - 5); 
            document.getElementById('puntos').innerText = puntosBase;
            
            reproducirSonido('incorrecto');
            
            const txtBurbuja = document.getElementById('burbuja');
            txtBurbuja.style.color = "var(--rosa)";
            txtBurbuja.innerText = "INCORRECTO VUELVE A INTENTARLO";

            setTimeout(generarNuevaActividad, 1400);
        }

        // Pantalla final y evaluación de logros obtenidos estrictamente de 0 a 100%
        function finalizarJuego() {
            if (temporizador) clearInterval(temporizador);
            cambiarPantalla('pantalla-final');
            reproducirSonido('final');

            // El porcentaje se calcula de manera justa en base a los aciertos y penalizaciones
            // 12 aciertos perfectos = 120 puntos base = 100% de la nota matemática.
            let notaFinal = Math.round((puntosBase / 120) * 100);
            if (notaFinal > 100) notaFinal = 100;
            if (notaFinal < 0) notaFinal = 0;

            document.getElementById('res-correctas').innerText = correctasContadas;
            document.getElementById('res-incorrectas').innerText = incorrectasContadas;
            document.getElementById('res-nota').innerText = `${notaFinal}%`;

            const medalla = document.getElementById('logro-medalla');
            const titulo = document.getElementById('logro-titulo');
            const desc = document.getElementById('logro-descripcion');

            // Ajustar nota final de acuerdo a los aciertos y fallos acumulados
            if (notaFinal === 100) {
                medalla.innerText = '👑';
                titulo.innerText = '¡Perfecto Absoluto! (100%)';
                desc.innerText = `¡Espectacular rendimiento sin fallos! Tu nota es perfecta.`;
            } else if (notaFinal >= 80) {
                medalla.innerText = '🥇';
                titulo.innerText = `Rango Sobresaliente (${notaFinal}%)`;
                desc.innerText = `¡Excelente! Dominas las operaciones con fluidez en el laberinto.`;
            } else if (notaFinal >= 60) {
                medalla.innerText = '🥈';
                titulo.innerText = `Rango Aprobado (${notaFinal}%)`;
                desc.innerText = `¡Buen trabajo! Superaste las pruebas pero debes cuidar no confundirte para no perder puntos.`;
            } else {
                medalla.innerText = '🥉';
                titulo.innerText = `Rango Insuficiente (${notaFinal}%)`;
                desc.innerText = `¡No te rindas! Los errores penalizaron tu nota. Inténtalo de nuevo para mejorar.`;
            }
        }
    </script>
<a href="https://matheken2.netlify.app/" target="_blank" class="btn-flotante-mateken">
    🤖 Ir a MateKen2
</a>
</body>
</html>

