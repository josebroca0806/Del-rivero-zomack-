<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Del Rivero Zomack - Abogados</title>
    <!-- Carga de Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc; /* Tailwind's slate-50 */
        }
        /* Estilos adicionales para la imagen de héroe */
        .hero-image {
            max-width: 80%; /* Ajusta el tamaño máximo de la imagen */
            height: auto;
            margin-bottom: 2rem;
            border-radius: 0.75rem; /* rounded-xl */
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05); /* shadow-lg */
        }
        @media (min-width: 768px) {
            .hero-image {
                max-width: 50%; /* Más grande en desktop */
            }
        }

        /* Estilos para el modal */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7); /* Fondo oscuro semitransparente */
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000; /* Asegura que esté por encima de todo */
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease, visibility 0.3s ease;
        }
        .modal-overlay.open {
            opacity: 1;
            visibility: visible;
        }
        .modal-content {
            background-color: white;
            padding: 2rem;
            border-radius: 0.75rem; /* rounded-xl */
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04); /* shadow-2xl */
            max-width: 90%;
            width: 500px; /* Ancho fijo para el modal */
            position: relative;
            transform: translateY(-20px);
            transition: transform 0.3s ease;
        }
        .modal-overlay.open .modal-content {
            transform: translateY(0);
        }
        .modal-close-button {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: #4B5563; /* gray-600 */
            transition: color 0.2s ease;
        }
        .modal-close-button:hover {
            color: #1F2937; /* gray-900 */
        }
        /* Estilos para el mapa */
        .map-container {
            position: relative;
            width: 100%;
            padding-bottom: 75%; /* Proporción 4:3 para el mapa */
            height: 0;
            overflow: hidden;
            border-radius: 0.75rem; /* rounded-xl */
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06); /* shadow-md */
        }
        .map-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: 0;
        }
    </style>
</head>
<body class="antialiased text-gray-800">

    <!-- Encabezado -->
    <header class="bg-gray-900 text-white shadow-lg py-4 px-6 md:px-12 rounded-b-lg">
        <div class="container mx-auto flex flex-col md:flex-row items-center justify-between">
            <h1 class="text-3xl font-bold mb-2 md:mb-0 text-center md:text-left">Del Rivero Zomack</h1>
            <nav class="mt-3 md:mt-0">
                <ul class="flex flex-wrap justify-center md:justify-end space-x-4 md:space-x-8 text-lg">
                    <li><a href="#inicio" class="hover:text-red-200 transition duration-300 ease-in-out">Inicio</a></li>
                    <li><a href="#servicios" class="hover:text-red-200 transition duration-300 ease-in-out">Servicios</a></li>
                    <li><a href="#nosotros" class="hover:text-red-200 transition duration-300 ease-in-out">Nosotros</a></li>
                    <li><a href="#contacto" class="hover:text-red-200 transition duration-300 ease-in-out">Contacto</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Sección de Héroe/Inicio con la imagen principal -->
    <section id="inicio" class="relative bg-gradient-to-r from-red-800 to-red-900 text-white py-20 px-6 md:py-32 md:px-12 rounded-b-lg flex flex-col items-center justify-center">
        <div class="container mx-auto text-center">
            <!-- Imagen del logo principal (ruta actualizada) -->
            <img src="image.png-c74658ed-9dc3-4139-9e1b-bb2bd1b0f100" alt="Del Rivero Zomack Logo Principal" class="hero-image mx-auto">

            <h2 class="text-4xl md:text-5xl font-extrabold leading-tight mb-6">
                Expertos en Asesoría Legal
            </h2>
            <p class="text-lg md:text-xl mb-8 max-w-3xl mx-auto">
                Brindamos soluciones jurídicas integrales con profesionalismo y compromiso. Su tranquilidad es nuestra prioridad.
            </p>
            <!-- Botón que abre el modal -->
            <button id="openContactModal" class="bg-white text-red-900 hover:bg-gray-100 font-bold py-3 px-8 rounded-full shadow-lg transition duration-300 ease-in-out transform hover:scale-105">
                Contáctenos Hoy
            </button>
        </div>
    </section>

    <!-- Sección de Servicios -->
    <section id="servicios" class="py-16 px-6 md:py-24 md:px-12 bg-white rounded-lg shadow-md mx-4 md:mx-auto my-8 max-w-7xl">
        <div class="container mx-auto">
            <h2 class="text-3xl md:text-4xl font-bold text-center mb-12 text-red-900">Nuestros Servicios</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Tarjeta de Servicio 1 -->
                <div class="bg-red-50 p-6 rounded-xl shadow-md border border-red-200 flex flex-col items-center text-center transform transition duration-300 hover:scale-105 hover:shadow-xl">
                    <div class="text-red-600 mb-4 text-5xl">
                        &#9874; <!-- Escala de justicia unicode -->
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-red-800">Derecho Civil</h3>
                    <p class="text-gray-700">Asesoramiento y representación en casos de contratos, propiedades, herencias y más.</p>
                </div>
                <!-- Tarjeta de Servicio 2 -->
                <div class="bg-red-50 p-6 rounded-xl shadow-md border border-red-200 flex flex-col items-center text-center transform transition duration-300 hover:scale-105 hover:shadow-xl">
                    <div class="text-red-600 mb-4 text-5xl">
                        &#128188; <!-- Maletín unicode -->
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-red-800">Derecho Mercantil</h3>
                    <p class="text-gray-700">Constitución de sociedades, contratos mercantiles, litigios comerciales y disoluciones.</p>
                </div>
                <!-- Tarjeta de Servicio 3 -->
                <div class="bg-red-50 p-6 rounded-xl shadow-md border border-red-200 flex flex-col items-center text-center transform transition duration-300 hover:scale-105 hover:shadow-xl">
                    <div class="text-red-600 mb-4 text-5xl">
                        &#128083; <!-- Martillo de juez unicode -->
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-red-800">Derecho Familiar</h3>
                    <p class="text-gray-700">Divorcios, pensiones alimenticias, custodias y régimen de visitas.</p>
                </div>
                <!-- Tarjeta de Servicio 4 -->
                <div class="bg-red-50 p-6 rounded-xl shadow-md border border-red-200 flex flex-col items-center text-center transform transition duration-300 hover:scale-105 hover:shadow-xl">
                    <div class="text-red-600 mb-4 text-5xl">
                        &#128220; <!-- Documento unicode -->
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-red-800">Asesoría Corporativa</h3>
                    <p class="text-gray-700">Soporte legal para empresas, cumplimiento normativo y estrategia legal.</p>
                </div>
                <!-- Tarjeta de Servicio 5 -->
                <div class="bg-red-50 p-6 rounded-xl shadow-md border border-red-200 flex flex-col items-center text-center transform transition duration-300 hover:scale-105 hover:shadow-xl">
                    <div class="text-red-600 mb-4 text-5xl">
                        &#128269; <!-- Lupa unicode -->
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-red-800">Litigio General</h3>
                    <p class="text-gray-700">Defensa y representación en diversas áreas del derecho.</p>
                </div>
                <!-- Tarjeta de Servicio 6 -->
                <div class="bg-red-50 p-6 rounded-xl shadow-md border border-red-200 flex flex-col items-center text-center transform transition duration-300 hover:scale-105 hover:shadow-xl">
                    <div class="text-red-600 mb-4 text-5xl">
                        &#128205; <!-- Marcador de mapa unicode -->
                    </div>
                    <h3 class="text-xl font-semibold mb-3 text-red-800">Derecho Inmobiliario</h3>
                    <p class="text-gray-700">Asesoría en compra-venta, arrendamientos y regularización de inmuebles.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Sección Sobre Nosotros -->
    <section id="nosotros" class="py-16 px-6 md:py-24 md:px-12 bg-gray-100 rounded-lg shadow-md mx-4 md:mx-auto my-8 max-w-7xl">
        <div class="container mx-auto flex flex-col md:flex-row items-center gap-8">
            <div class="md:w-1/2">
                <img src="https://placehold.co/600x400/BFDBFE/1E3A8A?text=Equipo+Legal" alt="Equipo Legal Del Rivero Zomack" class="rounded-xl shadow-lg w-full h-auto object-cover">
            </div>
            <div class="md:w-1/2 text-center md:text-left">
                <h2 class="text-3xl md:text-4xl font-bold mb-6 text-red-900">Acerca de Del Rivero Zomack</h2>
                <p class="text-lg leading-relaxed text-gray-700 mb-4">
                    En Del Rivero Zomack, somos un despacho jurídico comprometido con la excelencia y la ética. Contamos con un equipo de abogados altamente calificados, dedicados a ofrecer soluciones legales personalizadas y efectivas para cada uno de nuestros clientes.
                </p>
                <p class="text-lg leading-relaxed text-gray-700">
                    Nuestra misión es proteger sus intereses, brindándole la mejor representación y asesoramiento en diversas ramas del derecho. Nos enorgullece construir relaciones de confianza y lograr resultados favorables.
                </p>
            </div>
        </div>
    </section>

    <!-- Sección de Contacto -->
    <section id="contacto" class="py-16 px-6 md:py-24 md:px-12 bg-gray-900 text-white rounded-lg shadow-md mx-4 md:mx-auto my-8 max-w-7xl">
        <div class="container mx-auto text-center">
            <h2 class="text-3xl md:text-4xl font-bold mb-8">Contáctenos</h2>
            <p class="text-lg md:text-xl mb-8">
                Puede comunicarse con nosotros a través de los siguientes medios:
            </p>
            <div class="flex flex-col md:flex-row justify-center items-center gap-6 mb-8">
                <a href="tel:+529932846857" class="flex items-center bg-white text-red-900 hover:bg-gray-100 font-bold py-3 px-6 rounded-full shadow-lg transition duration-300 ease-in-out transform hover:scale-105">
                    <span class="mr-3 text-2xl">&#9742;</span> Llamar: (993) 284 6857
                </a>
            </div>

            <p class="text-lg md:text-xl mb-4">
                Encuéntrenos en redes sociales:
            </p>
            <div class="flex justify-center space-x-6 mb-8">
                <a href="https://www.facebook.com/share/1ZaQmLXLZP/" target="_blank" class="text-white hover:text-red-200 transition duration-300 ease-in-out">
                    <!-- Icono de Facebook (SVG) -->
                    <svg class="w-10 h-10" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                        <path fill-rule="evenodd" d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33V22C18.343 21.128 22 16.991 22 12z" clip-rule="evenodd" />
                    </svg>
                </a>
                <!-- Enlace de WhatsApp con logo SVG más detallado -->
                <a href="https://wa.me/529932846857" target="_blank" class="text-white hover:text-red-200 transition duration-300 ease-in-out">
                    <svg class="w-10 h-10" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                        <path d="M12.04 2C7.385 2 3.5 5.885 3.5 10.54s3.885 8.54 8.54 8.54c1.996 0 3.843-.72 5.263-2.025l2.454.818-1.5-2.335A8.47 8.47 0 0 0 20.54 10.54c0-4.655-3.885-8.54-8.54-8.54zm-1.09 13.91s-.517-.26-1.52-.733c-1.003-.473-1.66-1.206-1.92-1.467-.26-.26-1.996-2.617-1.996-4.912 0-2.327 1.196-3.418 1.57-3.72.373-.303.79-.387 1.05-.387.26 0 .373 0 .584.008.21.008.31.025.465.387.155.362.535 1.285.584 1.398.049.113.083.24.016.425-.067.184-.447.46-.584.62-.138.16-.29.355-.43.515-.138.155-.29.33-.2.49.09.16.63.98.905 1.48.275.5.51.643.67.708.16.065.29.055.4.016.11-.04.72-.295.91-.48.19-.18.32-.303.46-.387.14-.084.275-.075.46-.016.185.058 1.196.56 1.446.68.25.12.41.18.52.275.11.095.66.413.75.473.09.06.14.07.24.075.1.005.65.22.74.26.09.04.2.06.31.06.11 0 .61-.22.7-.26.09-.04.2-.07.31-.07.11 0 .6-.21.75-.26.15-.05.28-.06-.4-.06.12 0 .5-.01.5-.01s.035-.008.103.016c.068.025.155.12.21.275.055.155.18.5.18.5s-.08.2-.18.25c-.1.05-.2.07-.31.07-.11 0-.61-.22-.7-.26-.09-.04-.2-.07-.31-.07-.11 0-.6-.21-.75-.26-.15-.05-.28-.06-.4-.06z"/>
                    </svg>
                </a>
            </div>

            <p class="text-lg md:text-xl mb-4">
                Estamos ubicados en:
            </p>
            <p class="text-xl md:text-2xl font-semibold mb-8">
                Fraccionamiento Lidia Esther, Calle José Martí 101, Villahermosa, Tabasco.
            </p>

            <!-- Mini-mapa de Google Maps -->
            <div class="map-container">
                <iframe
                    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3790.228026117978!2d-92.9308076239103!3d17.99606419759714!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x85edd7f22317e34b%3A0x7124bbaba50ed48a!2sAbogado+Lic.+Jos%C3%A9+Carlos+De+La+fuente+H.!5e0!3m2!1ses-419!2smx!4v1700000000000!5m2!1ses-419!2smx"
                    allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade">
                </iframe>
            </div>
        </div>
    </section>

    <!-- Pie de Página -->
    <footer class="bg-gray-800 text-white py-6 px-6 md:px-12 mt-8 rounded-t-lg">
        <div class="container mx-auto text-center text-sm">
            <p>&copy; 2023 Del Rivero Zomack. Todos los derechos reservados.</p>
            <p class="mt-2">Diseñado con ❤️ para la comunidad.</p>
        </div>
    </footer>

    <!-- Modal de Contacto -->
    <div id="contactModal" class="modal-overlay">
        <div class="modal-content">
            <button id="closeModal" class="modal-close-button">&times;</button>
            <h3 class="text-2xl font-bold text-red-900 mb-4 text-center">Contáctenos Directamente</h3>
            <p class="text-gray-700 text-center mb-4">Estamos a su disposición para cualquier consulta legal.</p>

            <div class="flex flex-col items-center gap-4">
                <p class="text-lg font-semibold text-gray-800">
                    <span class="mr-2 text-red-600">&#128205;</span> Fraccionamiento Lidia Esther, Calle José Martí 101, Villahermosa, Tabasco.
                </p>
                <a href="tel:+529932846857" class="flex items-center bg-red-700 text-white hover:bg-red-800 font-bold py-2 px-5 rounded-full shadow-md transition duration-300 ease-in-out transform hover:scale-105">
                    <span class="mr-3 text-xl">&#9742;</span> Llamar: (993) 284 6857
                </a>
                <!-- Enlace de WhatsApp en el modal -->
                <a href="https://wa.me/529932846857" target="_blank" class="flex items-center bg-green-500 text-white hover:bg-green-600 font-bold py-2 px-5 rounded-full shadow-md transition duration-300 ease-in-out transform hover:scale-105">
                    <svg class="mr-3 w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                        <path d="M12.04 2C7.385 2 3.5 5.885 3.5 10.54s3.885 8.54 8.54 8.54c1.996 0 3.843-.72 5.263-2.025l2.454.818-1.5-2.335A8.47 8.47 0 0 0 20.54 10.54c0-4.655-3.885-8.54-8.54-8.54zm-1.09 13.91s-.517-.26-1.52-.733c-1.003-.473-1.66-1.206-1.92-1.467-.26-.26-1.996-2.617-1.996-4.912 0-2.327 1.196-3.418 1.57-3.72.373-.303.79-.387 1.05-.387.26 0 .373 0 .584.008.21.008.31.025.465.387.155.362.535 1.285.584 1.398.049.113.083.24.016.425-.067.184-.447.46-.584.62-.138.16-.29.355-.43.515-.138.155-.29.33-.2.49.09.16.63.98.905 1.48.275.5.51.643.67.708.16.065.29.055.4.016.11-.04.72-.295.91-.48.19-.18.32-.303.46-.387.14-.084.275-.075.46-.016.185.058 1.196.56 1.446.68.25.12.41.18.52.275.11.095.66.413.75.473.09.06.14.07.24.075.1.005.65.22.74.26.09.04.2.06.31.06.11 0 .61-.22.7-.26.09-.04.2-.07.31-.07.11 0 .6-.21.75-.26.15-.05.28-.06-.4-.06.12 0 .5-.01.5-.01s.035-.008.103.016c.068.025.155.12.21.275.055.155.18.5.18.5s-.08.2-.18.25c-.1.05-.2.07-.31.07-.11 0-.61-.22-.7-.26-.09-.04-.2-.07-.31-.07-.11 0-.6-.21-.75-.26-.15-.05-.28-.06-.4-.06z"/>
                    </svg>
                    WhatsApp
                </a>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const openModalButton = document.getElementById('openContactModal');
            const contactModal = document.getElementById('contactModal');
            const closeModalButton = document.getElementById('closeModal');

            // Función para abrir el modal
            openModalButton.addEventListener('click', () => {
                contactModal.classList.add('open');
            });

            // Función para cerrar el modal al hacer clic en el botón de cerrar
            closeModalButton.addEventListener('click', () => {
                contactModal.classList.remove('open');
            });

            // Función para cerrar el modal al hacer clic fuera del contenido del modal
            contactModal.addEventListener('click', (event) => {
                if (event.target === contactModal) {
                    contactModal.classList.remove('open');
                }
            });
        });
    </script>

</body>
</html>

