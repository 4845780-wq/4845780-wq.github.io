
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Urban Shoes | Tienda de zapatos</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f4f4f4;
            color: #222;
        }

        header {
            background: #111;
            color: white;
            padding: 20px 7%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            color: #f5b400;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 0 10px;
        }

        nav a:hover {
            color: #f5b400;
        }

        .carrito {
            background: #f5b400;
            color: #111;
            padding: 10px 15px;
            border-radius: 6px;
            font-weight: bold;
        }

        .hero {
            min-height: 400px;
            background: linear-gradient(90deg, #111, #444);
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 40px 20px;
        }

        .hero h1 {
            font-size: 48px;
            margin-bottom: 15px;
        }

        .hero p {
            font-size: 19px;
            margin-bottom: 25px;
        }

        .boton {
            background: #f5b400;
            color: #111;
            padding: 13px 25px;
            text-decoration: none;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
        }

        .boton:hover {
            background: white;
        }

        section {
            padding: 55px 7%;
        }

        .titulo {
            text-align: center;
            font-size: 32px;
            margin-bottom: 30px;
        }

        .controles {
            display: flex;
            justify-content: center;
            gap: 12px;
            flex-wrap: wrap;
            margin-bottom: 30px;
        }

        input, select {
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 6px;
        }

        .productos {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
        }

        .producto {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 3px 12px #00000015;
            text-align: center;
            padding-bottom: 20px;
            transition: 0.3s;
        }

        .producto:hover {
            transform: translateY(-5px);
        }

        .producto img {
            width: 100%;
            height: 190px;
            object-fit: cover;
        }

        .producto h3 {
            margin: 15px 0 8px;
        }

        .precio {
            color: #b47d00;
            font-size: 21px;
            font-weight: bold;
            margin: 12px;
        }

        .producto button {
            margin: 5px;
        }

        .favorito {
            background: #eee;
            border: none;
            padding: 10px;
            border-radius: 6px;
            cursor: pointer;
        }

        .favorito.activo {
            background: #ffd9d9;
            color: red;
        }

        .sobre {
            background: #fff;
            text-align: center;
            line-height: 1.8;
        }

        .sobre p {
            max-width: 750px;
            margin: auto;
        }

        .contacto {
            text-align: center;
            line-height: 2;
        }

        footer {
            background: #111;
            color: white;
            text-align: center;
            padding: 25px;
        }

        .carrito-contenido {
            background: white;
            padding: 20px;
            border-radius: 10px;
            max-width: 700px;
            margin: auto;
        }

        .item-carrito {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 10px;
            padding: 12px 0;
            border-bottom: 1px solid #ddd;
        }

        .item-carrito button {
            padding: 5px 10px;
            cursor: pointer;
        }

        .total {
            text-align: right;
            font-size: 22px;
            font-weight: bold;
            margin-top: 20px;
        }

        @media(max-width: 600px) {
            .hero h1 {
                font-size: 34px;
            }

            header {
                justify-content: center;
            }
        }
    </style>
</head>

<body>

    <header>
        <div class="logo">URBAN SHOES</div>

        <nav>
            <a href="#inicio">Inicio</a>
            <a href="#productos">Productos</a>
            <a href="#nosotros">Nosotros</a>
            <a href="#contacto">Contacto</a>
        </nav>

        <div class="carrito">
            🛒 Carrito: <span id="cantidad">0</span>
        </div>
    </header>

    <section class="hero" id="inicio">
        <h1>CAMINA CON ESTILO</h1>
        <p>Encuentra los mejores zapatos para cada ocasión.</p>
        <a href="#productos" class="boton">VER PRODUCTOS</a>
    </section>

    <section id="productos">
        <h2 class="titulo">NUESTROS PRODUCTOS</h2>

        <div class="controles">
            <input type="text" id="busqueda"
                placeholder="Buscar zapatos..."
                oninput="mostrarProductos()">

            <select id="categoria" onchange="mostrarProductos()">
                <option value="todos">Todas las categorías</option>
                <option value="deportivos">Deportivos</option>
                <option value="casuales">Casuales</option>
                <option value="urbanos">Urbanos</option>
            </select>

            <select id="orden" onchange="mostrarProductos()">
                <option value="normal">Ordenar por</option>
                <option value="menor">Precio menor</option>
                <option value="mayor">Precio mayor</option>
                <option value="nombre">Nombre</option>
            </select>
        </div>

        <div class="productos" id="listaProductos"></div>
    </section>

    <section id="carrito">
        <h2 class="titulo">MI CARRITO</h2>

        <div class="carrito-contenido">
            <div id="listaCarrito">
                Tu carrito está vacío.
            </div>

            <div class="total">
                Total: $<span id="total">0.00</span>
            </div>

            <button class="boton" onclick="finalizarCompra()">
                FINALIZAR COMPRA
            </button>
        </div>
    </section>

    <section class="sobre" id="nosotros">
        <h2 class="titulo">SOBRE NOSOTROS</h2>

        <p>
            En Urban Shoes nos dedicamos a ofrecer zapatos modernos,
            cómodos y de excelente estilo. Queremos que cada cliente
            encuentre el calzado perfecto para expresar su personalidad.
            Nuestra tienda cuenta con diferentes estilos para jóvenes
            y adultos.
        </p>
    </section>

    <section class="contacto" id="contacto">
        <h2 class="titulo">CONTÁCTANOS</h2>

        <p>📍 El Salvador</p>
        <p>📧 urbanshoes@gmail.com</p>
        <p>📞 7000-0000</p>
        <p>Horario: Lunes a sábado, 8:00 a. m. - 6:00 p. m.</p>

        <br>

        <h3>Suscríbete a nuestras novedades</h3>

        <input type="email" id="correo"
            placeholder="Escribe tu correo">

        <button class="boton" onclick="suscribirse()">
            SUSCRIBIRME
        </button>
    </section>

    <footer>
        <p>© 2026 Urban Shoes - Todos los derechos reservados.</p>
        <p>Calidad, comodidad y estilo en cada paso.</p>
    </footer>

    <script>
        const productos = [
            {
                nombre: "Nike Air Force 1",
                precio: 85,
                categoria: "urbanos",
                imagen: "img air force 1.webp"
            },
            {
                nombre: "Adidas Running",
                precio: 70,
                categoria: "deportivos",
                imagen: "img adidas running.jpg"
            },
            {
                nombre: "Zapatos Urbanos",
                precio: 55,
                categoria: "urbanos",
                imagen: "https://images.unsplash.com/photo-1495555961986-6d4c1ecb7be3?w=600"
            },
            {
                nombre: "Nike Deportivos",
                precio: 90,
                categoria: "deportivos",
                imagen: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=600"
            },
            {
                nombre: "Zapatos Casuales",
                precio: 45,
                categoria: "casuales",
                imagen: "img zapatos casuales.jpg"
            },
            {
                nombre: "Converse",
                precio: 60,
                categoria: "casuales",
                imagen: "img coverse.jpg"
            },
            {
                nombre: "Tenis Deportivos",
                precio: 75,
                categoria: "deportivos",
                imagen: "https://images.unsplash.com/photo-1552346154-21d32810aba3?w=600"
            },
            
            
        ];

        let carrito = [];

        function mostrarProductos() {
            const lista = document.getElementById("listaProductos");
            const busqueda = document.getElementById("busqueda").value.toLowerCase();
            const categoria = document.getElementById("categoria").value;
            const orden = document.getElementById("orden").value;

            let resultado = productos.filter(producto => {
                const coincideNombre = producto.nombre.toLowerCase().includes(busqueda);
                const coincideCategoria = categoria === "todos" ||
                    producto.categoria === categoria;

                return coincideNombre && coincideCategoria;
            });

            if (orden === "menor") {
                resultado.sort((a, b) => a.precio - b.precio);
            }

            if (orden === "mayor") {
                resultado.sort((a, b) => b.precio - a.precio);
            }

            if (orden === "nombre") {
                resultado.sort((a, b) => a.nombre.localeCompare(b.nombre));
            }

            lista.innerHTML = "";

            if (resultado.length === 0) {
                lista.innerHTML = "<p>No se encontraron productos.</p>";
                return;
            }

            resultado.forEach(producto => {
                const indice = productos.indexOf(producto);

                lista.innerHTML += `
                    <div class="producto">
                        <img src="${producto.imagen}" alt="${producto.nombre}">
                        <h3>${producto.nombre}</h3>
                        <p>Categoría: ${producto.categoria}</p>
                        <p class="precio">$${producto.precio.toFixed(2)}</p>

                        <button class="boton"
                            onclick="agregarCarrito(${indice})">
                            AGREGAR AL CARRITO
                        </button>

                        <button class="favorito"
                            onclick="favorito(this)">
                            ♡ Favorito
                        </button>
                    </div>
                `;
            });
        }

        function agregarCarrito(indice) {
            const producto = productos[indice];
            const existente = carrito.find(item => item.nombre === producto.nombre);

            if (existente) {
                existente.cantidad++;
            } else {
                carrito.push({
                    ...producto,
                    cantidad: 1
                });
            }

            actualizarCarrito();
        }

        function actualizarCarrito() {
            const lista = document.getElementById("listaCarrito");
            const cantidad = document.getElementById("cantidad");
            const totalTexto = document.getElementById("total");

            lista.innerHTML = "";

            let total = 0;
            let unidades = 0;

            if (carrito.length === 0) {
                lista.innerHTML = "Tu carrito está vacío.";
            }

            carrito.forEach((producto, indice) => {
                total += producto.precio * producto.cantidad;
                unidades += producto.cantidad;

                lista.innerHTML += `
                    <div class="item-carrito">
                        <span>${producto.nombre} ($${producto.precio})</span>

                        <span>
                            <button onclick="cambiarCantidad(${indice}, -1)">−</button>
                            ${producto.cantidad}
                            <button onclick="cambiarCantidad(${indice}, 1)">+</button>
                            <button onclick="eliminarProducto(${indice})">Eliminar</button>
                        </span>
                    </div>
                `;
            });

            cantidad.textContent = unidades;
            totalTexto.textContent = total.toFixed(2);
        }

        function cambiarCantidad(indice, cambio) {
            carrito[indice].cantidad += cambio;

            if (carrito[indice].cantidad <= 0) {
                carrito.splice(indice, 1);
            }

            actualizarCarrito();
        }

        function eliminarProducto(indice) {
            carrito.splice(indice, 1);
            actualizarCarrito();
        }

        function favorito(boton) {
            boton.classList.toggle("activo");

            if (boton.classList.contains("activo")) {
                boton.textContent = "♥ Favorito";
            } else {
                boton.textContent = "♡ Favorito";
            }
        }

        function finalizarCompra() {
            if (carrito.length === 0) {
                alert("Tu carrito está vacío.");
                return;
            }

            alert("¡Gracias por tu compra! Esta es una demostración, no se realizó ningún pago.");

            carrito = [];
            actualizarCarrito();
        }

        function suscribirse() {
            const correo = document.getElementById("correo").value;

            if (correo === "" || !correo.includes("@")) {
                alert("Escribe un correo electrónico válido.");
                return;
            }

            alert("¡Gracias por suscribirte a Urban Shoes!");
            document.getElementById("correo").value = "";
        }

        mostrarProductos();
    </script>

</body>
</html>

