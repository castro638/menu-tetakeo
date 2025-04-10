<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Menú Restaurante</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background-color: #f2f2f2; }
    h1, h2 { text-align: center; }
    .menu-item { background: #fff; padding: 15px; margin-bottom: 10px; border-radius: 8px; box-shadow: 0 0 5px rgba(0,0,0,0.1); }
    .precio { font-weight: bold; color: green; }
    .boton { display: inline-block; margin: 20px auto; padding: 10px 20px; background: #28a745; color: white; border: none; border-radius: 5px; cursor: pointer; text-align: center; }
    #mediosPago { display: none; text-align: center; margin-top: 30px; }
    .link-pago { display: block; margin: 10px auto; padding: 10px; background: #007bff; color: white; text-decoration: none; border-radius: 5px; max-width: 300px; }
  </style>
</head>
<body>
  <h1>Menú Restaurante</h1>
  <div id="menu"></div>
  <button class="boton" onclick="finalizarCompra()">Finalizar Compra</button>
  <div id="mediosPago">
    <h2>Medios de Pago</h2>
    <a href="https://www.nequi.com.co/" class="link-pago" target="_blank">Pagar con Nequi</a>
    <a href="https://www.daviplata.com/wps/portal/daviplata" class="link-pago" target="_blank">Pagar con Daviplata</a>
  </div>

  <script>
    const dia = new Date().getDay(); // 2 = martes
    const esMartes = dia === 2;

    const menu = [
      { nombre: "Hamburguesa Sencilla", descripcion: "Carne artesanal, queso doble crema, verduras (lechuga, tomate, cebolla caramelizada), salsas (tártara, ranchera, BBQ), pan artesanal.", precio: 10000 },
      { nombre: "Hamburguesa Especial", descripcion: "Carne artesanal, tocineta ahumada, huevo, queso doble crema, huevo de codorniz, verduras, salsas, pan artesanal.", precio: 15000 },
      { nombre: "Hamburguesa Tetakeo", descripcion: "Carne artesanal, pechuga a la plancha, tocineta, huevo, queso doble crema, huevo de codorniz, verduras, salsas, pan artesanal.", precio: 22000 },
      { nombre: "Perro Caliente", descripcion: "Salchipapa americana, cebolla caramelizada, papas cabello de ángel, queso campesino, salsas, pan artesanal.", precio: 8000 },
      { nombre: "Perro Especial Mechiperro", descripcion: "Salchipapa americana, carne esmechada, cebolla caramelizada, lechuga, papas cabello de ángel, queso campesino, salsas, pan artesanal.", precio: 15000 },
      { nombre: "Salchipapa Sencilla", descripcion: "Salchipapa americana, papas a la francesa, queso campesino, salsas.", precio: 10500 },
      { nombre: "Salchipapa Especial", descripcion: "Carne esmechada, salchicha americana, papas a la francesa, lechuga, tomate, queso campesino, huevos de codorniz, maíz tierno, salsas.", precio: 20500 },
      { nombre: "Salchipapa Especial de Pollo", descripcion: "Pollo, salchicha americana, papas a la francesa, lechuga, tomate, queso campesino, huevos de codorniz, salsas.", precio: 23500 },
      { nombre: "Picada", descripcion: "Carne de res, cerdo, pechuga, salchicha americana, papas a la francesa, lechuga, tomate, cebolla caramelizada, queso campesino, aguacate, huevo de codorniz, salsas.", precio: 35500 },
      { nombre: "Mazorca", descripcion: "Carne de res, cerdo, pechuga, papas cabello de ángel, maíz tierno, papas a la francesa, queso campesino, salsas.", precio: 35500 },
      { nombre: "Bebida Coca-Cola", descripcion: "Bebida personal Coca-Cola", precio: 4000 },
      { nombre: "Bebida Sprite", descripcion: "Bebida personal Sprite", precio: 4000 },
      { nombre: "Bebida Cuatro", descripcion: "Bebida personal Cuatro", precio: 4000 },
      { nombre: "Bebida Kola Román", descripcion: "Bebida personal Kola Román", precio: 4000 },
    ];

    const promocionesMartes = [
      { nombre: "Promo Martes: 2 Hamburguesas Sencillas", descripcion: "2 Hamburguesas por solo $18.000", precio: 18000 },
      { nombre: "Promo Martes: 2 Perros Calientes", descripcion: "2 Perros Calientes por $12.000", precio: 12000 },
      { nombre: "Promo Martes: Mazorcada Sencilla", descripcion: "Mazorcada sencilla por $22.500", precio: 22500 }
    ];

    const contenedorMenu = document.getElementById("menu");
    const lista = esMartes ? [...menu, ...promocionesMartes] : [];

    if (lista.length === 0) {
      contenedorMenu.innerHTML = "<p style='text-align:center;'>El menú está disponible solo los martes. ¡Vuelve pronto!</p>";
    } else {
      lista.forEach(item => {
        const div = document.createElement("div");
        div.className = "menu-item";
        div.innerHTML = `<h3>${item.nombre}</h3><p>${item.descripcion}</p><p class='precio'>$${item.precio.toLocaleString()}</p>`;
        contenedorMenu.appendChild(div);
      });
    }

    function finalizarCompra() {
      document.getElementById("mediosPago").style.display = "block";
      window.scrollTo(0, document.body.scrollHeight);
    }
  </script>
</body>
</html>
