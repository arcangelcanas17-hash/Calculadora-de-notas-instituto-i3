# Calculadora-de-notas-instituto-i3

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Notas Instituto i3</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 500px;
            margin: 40px auto;
            padding: 20px;
            background-color: #f4f4f4;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        label {
            display: block;
            margin-top: 15px;
            font-weight: bold;
        }
        input {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
        }
        button {
            width: 100%;
            padding: 12px;
            margin-top: 25px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        #resultado {
            margin-top: 25px;
            padding: 15px;
            border-radius: 5px;
            text-align: center;
            font-size: 18px;
            display: none;
        }
        .aprobado {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        .reprobado {
            background-color: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
    </style>
</head>
<body>

    <h1>📘 Calculadora de Notas Instituto i3</h1>

    <form id="formulario">
        <label for="nombre">Nombre del Estudiante:</label>
        <input type="text" id="nombre" placeholder="Ingrese su nombre" required>

        <label for="nota1">Nota 1:</label>
        <input type="number" id="nota1" min="0" max="5" step="0.1" placeholder="Ingrese la nota 1" required>

        <label for="nota2">Nota 2:</label>
        <input type="number" id="nota2" min="0" max="5" step="0.1" placeholder="Ingrese la nota 2" required>

        <label for="nota3">Nota 3:</label>
        <input type="number" id="nota3" min="0" max="5" step="0.1" placeholder="Ingrese la nota 3" required>

        <button type="button" onclick="calcular()">Calcular Promedio</button>
    </form>

    <div id="resultado"></div>

    <script>
        function calcular() {
            // Obtener los valores
            const nombre = document.getElementById("nombre").value.trim();
            const nota1 = parseFloat(document.getElementById("nota1").value);
            const nota2 = parseFloat(document.getElementById("nota2").value);
            const nota3 = parseFloat(document.getElementById("nota3").value);

            // Validar que todos los campos estén llenos
            if (!nombre || isNaN(nota1) || isNaN(nota2) || isNaN(nota3)) {
                alert("Por favor complete todos los campos correctamente.");
                return;
            }

            // Calcular el promedio
            const promedio = (nota1 + nota2 + nota3) / 3;

            // Redondear a 1 decimal
            const promedioRedondeado = promedio.toFixed(1);

            // Determinar si aprueba (generalmente se aprueba con 3.0 o más en escala 0-5)
            const aprobado = promedio >= 3.0;

            // Mostrar el resultado
            const resultadoDiv = document.getElementById("resultado");
            resultadoDiv.style.display = "block";

            if (aprobado) {
                resultadoDiv.className = "aprobado";
                resultadoDiv.innerHTML = `
                    <strong>${nombre}</strong><br>
                    Promedio: <strong>${promedioRedondeado}</strong><br>
                    ✅ ¡Aprobado!
                `;
            } else {
                resultadoDiv.className = "reprobado";
                resultadoDiv.innerHTML = `
                    <strong>${nombre}</strong><br>
                    Promedio: <strong>${promedioRedondeado}</strong><br>
                    ❌ Reprobado
                `;
            }
        }
    </script>

</body>
</html>
