# Horario-mundial-futbol-2026_2
Creacion mi proyecto del curso_2
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mundial 2026 - Horarios</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <header>
    <h1>⚽ Mundial 2026</h1>
    <p>Horarios en sede local, España peninsular y Canarias</p>
  </header>

  <main>

    <section class="filtros">
      <input type="text" id="buscador" placeholder="Buscar selección o ciudad...">
    </section>

    <section>
      <table>
        <thead>
          <tr>
            <th>Partido</th>
            <th>Ciudad</th>
            <th>Estadio</th>
            <th>Hora Local</th>
            <th>Hora Peninsular</th>
            <th>Hora Canarias</th>
          </tr>
        </thead>
        <tbody id="tablaPartidos"></tbody>
      </table>
    </section>

  </main>

  <footer>
    <p>Proyecto creado con GitHub Pages</p>
  </footer>

  <script src="app.js"></script>
</body>
</html>
* {

header {
  background: #111827;
  color: white;
  padding: 30px;
  text-align: center;
}

header h1 {
  margin-bottom: 10px;
}

main {
  max-width: 1200px;
  margin: auto;
  padding: 20px;
}

.filtros {
  margin-bottom: 20px;
}

#buscador {
  width: 100%;
  padding: 12px;
  font-size: 16px;
  border-radius: 8px;
  border: 1px solid #ccc;
}

table {
  width: 100%;
  border-collapse: collapse;
  background: white;
  border-radius: 10px;
  overflow: hidden;
}

thead {
  background: #2563eb;
  color: white;
}

th,
td {
  padding: 14px;
  text-align: center;
  border-bottom: 1px solid #e5e7eb;
}

tr:hover {
  background: #f3f4f6;
}

footer {
  text-align: center;
  padding: 20px;
  color: #666;
}

@media (max-width: 900px) {
  table {
    display: block;
    overflow-x: auto;
  }
}
const tabla = document.getElementById("tablaPartidos");
const buscador = document.getElementById("buscador");

let partidosGlobal = [];

function convertirHora(fechaUTC, zona) {
  return new Date(fechaUTC).toLocaleString("es-ES", {
    timeZone: zona,
    day: "2-digit",
    month: "2-digit",
    hour: "2-digit",
    minute: "2-digit"
  });
}

function renderizarPartidos(partidos) {
  tabla.innerHTML = "";

  partidos.forEach(partido => {

    const fila = document.createElement("tr");

    fila.innerHTML = `
      <td>
        ${partido.bandera1} ${partido.equipo1}<br>
        vs<br>
        ${partido.bandera2} ${partido.equipo2}
      </td>
      <td>${partido.ciudad}</td>
      <td>${partido.estadio}</td>
      <td>
        ${convertirHora(partido.fechaUTC, partido.zonaHoraria)}
      </td>
      <td>
        ${convertirHora(partido.fechaUTC, "Europe/Madrid")}
      </td>
      <td>
        ${convertirHora(partido.fechaUTC, "Atlantic/Canary")}
      </td>
    `;

    tabla.appendChild(fila);
  });
}

fetch("partidos.json")
  .then(res => res.json())
  .then(data => {
    partidosGlobal = data;
    renderizarPartidos(data);
  });

buscador.addEventListener("input", e => {

  const texto = e.target.value.toLowerCase();

  const filtrados = partidosGlobal.filter(partido => {

    return (
      partido.equipo1.toLowerCase().includes(texto) ||
      partido.equipo2.toLowerCase().includes(texto) ||
});
[
  {
    "equipo1": "España",
    "bandera1": "🇪🇸",
    "equipo2": "Brasil",
    "bandera2": "🇧🇷",
    "ciudad": "Nueva York",
    "estadio": "MetLife Stadium",
    "pais": "Estados Unidos",
    "fechaUTC": "2026-06-15T00:00:00Z",
    "zonaHoraria": "America/New_York"
  },
  {
    "equipo1": "Argentina",
    "bandera1": "🇦🇷",
    "equipo2": "México",
    "bandera2": "🇲🇽",
    "ciudad": "Ciudad de México",
    "estadio": "Estadio Azteca",
    "pais": "México",
    "fechaUTC": "2026-06-16T02:00:00Z",
    "zonaHoraria": "America/Mexico_City"
  },
  {
    "equipo1": "Portugal",
    "bandera1": "🇵🇹",
    "equipo2": "Francia",
    "bandera2": "🇫🇷",
    "ciudad": "Toronto",
    "estadio": "BMO Field",
    "pais": "Canadá",
    "fechaUTC": "2026-06-18T18:00:00Z",
    "zonaHoraria": "America/Toronto"
  },
  {
    "equipo1": "Alemania",
    "bandera1": "🇩🇪",
    "equipo2": "Inglaterra",
    "bandera2": "🏴",
    "ciudad": "Los Ángeles",
    "estadio": "SoFi Stadium",
    "pais": "Estados Unidos",
    "fechaUTC": "2026-06-20T03:00:00Z",
    "zonaHoraria": "America/Los_Angeles"
  }
]
# Mundial 2026 - Horarios

Web creada con HTML, CSS y JavaScript para consultar:

- Horarios de partidos
- Hora local de cada sede
- Hora peninsular española
- Hora canaria
- Equipos participantes
- Estadios y ciudades

## Publicar en GitHub Pages

1. Crear un repositorio en GitHub
2. Subir todos los archivos
3. Ir a:

Settings → Pages

4. Activar:

Deploy from branch

5. Seleccionar:

main / root

6. Guardar

Tu web estará disponible en:

https://Melchor18.github.io/mundial-horarios
