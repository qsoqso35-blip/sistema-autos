<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Custodia Metropolitana</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #0f172a;
      color: white;
      margin: 0;
      padding: 0;
    }
    header {
      background: #1e293b;
      padding: 20px;
      text-align: center;
      font-size: 24px;
      font-weight: bold;
    }
    .container {
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }
    input, button {
      padding: 10px;
      margin: 5px 0;
      width: 100%;
      border: none;
      border-radius: 5px;
    }
    input {
      background: #334155;
      color: white;
    }
    button {
      background: #2563eb;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background: #1d4ed8;
    }
    .card {
      background: #1e293b;
      padding: 15px;
      margin-top: 10px;
      border-radius: 10px;
    }
  </style>
</head>
<body>

<header>
  Custodia Metropolitana - Registro de Automóviles
</header>

<div class="container">

  <h2>Registrar Automóvil</h2>
  <input type="text" id="patente" placeholder="Patente">
  <input type="text" id="marca" placeholder="Marca">
  <input type="text" id="modelo" placeholder="Modelo">
  <input type="number" id="anio" placeholder="Año">
  <input type="number" id="precio" placeholder="Precio CLP">
  <button onclick="registrarAuto()">Registrar</button>

  <h2>Buscar por Patente</h2>
  <input type="text" id="buscar" placeholder="Ingresa patente">
  <button onclick="buscarAuto()">Buscar</button>

  <div id="resultado"></div>

</div>

<script>
  let autos = [];

  function registrarAuto() {
    let auto = {
      patente: document.getElementById("patente").value,
      marca: document.getElementById("marca").value,
      modelo: document.getElementById("modelo").value,
      anio: document.getElementById("anio").value,
      precio: document.getElementById("precio").value
    };

    autos.push(auto);
    alert("Automóvil registrado correctamente");
  }

  function buscarAuto() {
    let patente = document.getElementById("buscar").value;
    let resultado = document.getElementById("resultado");

    let auto = autos.find(a => a.patente === patente);

    if (auto) {
      resultado.innerHTML = `
        <div class="card">
          <h3>${auto.marca} ${auto.modelo}</h3>
          <p><b>Patente:</b> ${auto.patente}</p>
          <p><b>Año:</b> ${auto.anio}</p>
          <p><b>Precio:</b> $${auto.precio}</p>
        </div>
      `;
    } else {
      resultado.innerHTML = "<p>No encontrado</p>";
    }
  }
</script>

</body>
</html>
