Fecha 20260903
Herramienta de IA: Claude
Prompt utilizado:  Crea un HTML5 semántico para una sección de favoritos, para el HTML  anexo a este prompt. Este debe de incluir título, lista de recursos seleccionados como favoritos con imagen, título, descripción y fecha. Ni uses div  para nada, sóo usa las etiquetas semánticas de HTML.  Esta sección de favoritos me gustaría que fuera un slide que contiene 5 artículos más consultador por los estudiantes en el sitio webs la etiqueta div; utiliza exclusivamente etiquetas semánticas de HTML5."

Razones por las cuales no usar este dódigo: El código que me arrojó claude no lo puedo utilizar ya que incluye CSS, así como Javascript, también lo tuve que modificar ya que sin la indicación de que era una sección conjunta me agregaba el header y el footer en ea misma sección como si estuviera dentro de ese contenedor. 
<!-- ============================================================
     SECCIÓN FAVORITOS — Hub de Recursos Educativos
     Reemplaza el bloque <section id="Favoritos"> de index.html
     Carrusel de los 5 recursos más consultados. Sin <div>.
     ============================================================ -->

<section id="Favoritos" aria-labelledby="favoritos-titulo">

    <h2 id="favoritos-titulo">Favoritos</h2>
    <p>Los cinco recursos que los estudiantes del posgrado consultan con más frecuencia.</p>

    <ol id="favoritos-carrusel" tabindex="0" aria-labelledby="favoritos-titulo">

        <li>
            <article>
                <img src="./assets/favoritos.png" alt="Consulta Bibliográfica">
                <h3>Consulta Bibliográfica</h3>
                <p>Busca artículos, tesis y libros académicos en Google Académico</p>
                <time datetime="2026-03-24">24 de marzo de 2026</time>
                <a href="https://enlace.com" target="_blank" rel="noopener"
                   aria-label="Enlace a Consulta Bibliográfica">Enlace</a>
            </article>
        </li>

        <li>
            <article>
                <img src="./assets/citasapa.png" alt="Tutorial para citas en APA">
                <h3>Tutorial para citas en APA</h3>
                <p>Guía en español para citar y armar tu lista de referencias con el formato APA</p>
                <time datetime="2026-07-03">3 de julio de 2026</time>
                <a href="https://enlace.com" target="_blank" rel="noopener"
                   aria-label="Enlace a Tutorial para citas en APA">Enlace</a>
            </article>
        </li>

        <li>
            <article>
                <img src="./assets/tutorial.png" alt="Tutorial para enviar tu Tesis">
                <h3>Tutorial para enviar tu Tesis</h3>
                <p>Guía paso a paso para preparar y enviar tu tesis</p>
                <time datetime="2026-06-15">15 de junio de 2026</time>
                <a href="https://enlace.com" target="_blank" rel="noopener"
                   aria-label="Enlace a Tutorial para enviar tu Tesis">Enlace</a>
            </article>
        </li>

        <li>
            <article>
                <img src="./assets/basesdedatos.png" alt="Acceso remoto a bases de datos">
                <h3>Acceso remoto a bases de datos</h3>
                <p>Configura la conexión institucional para consultar JSTOR y EBSCO desde casa</p>
                <time datetime="2026-05-22">22 de mayo de 2026</time>
                <a href="https://enlace.com" target="_blank" rel="noopener"
                   aria-label="Enlace a Acceso remoto a bases de datos">Enlace</a>
            </article>
        </li>

        <li>
            <article>
                <img src="./assets/repositorio.png" alt="Repositorio de tesis del posgrado">
                <h3>Repositorio de tesis del posgrado</h3>
                <p>Consulta tesis aprobadas de generaciones anteriores como referencia de formato</p>
                <time datetime="2026-04-09">9 de abril de 2026</time>
                <a href="https://enlace.com" target="_blank" rel="noopener"
                   aria-label="Enlace a Repositorio de tesis del posgrado">Enlace</a>
            </article>
        </li>

    </ol>

    <nav aria-label="Control del carrusel de favoritos">
        <button type="button" aria-controls="favoritos-carrusel" data-favoritos-anterior>Anterior</button>
        <button type="button" aria-controls="favoritos-carrusel" data-favoritos-siguiente>Siguiente</button>
    </nav>

    <p role="status" hidden data-favoritos-vacio>
        Todavía no hay recursos destacados. Vuelve más tarde o
        <a href="mailto:recursos@universidad.edu">sugiere uno por correo</a>.
    </p>

</section>


<!-- CSS: muévelo a tu hoja de estilos. Es lo mínimo que convierte
     la lista en un carrusel; el desplazamiento funciona sin JavaScript. -->
<style>
    #favoritos-carrusel {
        display: flex;
        gap: 1.5rem;
        overflow-x: auto;
        scroll-snap-type: x mandatory;
        scroll-padding-inline: 1rem;
        scroll-behavior: smooth;
        list-style: none;
        margin: 1.5rem 0 0;
        padding: 0 0 1rem;
        counter-reset: favorito;
    }
    #favoritos-carrusel > li {
        flex: 0 0 clamp(15rem, 70vw, 20rem);
        scroll-snap-align: start;
        counter-increment: favorito;
    }
    #favoritos-carrusel > li::before {
        content: counter(favorito);
        display: block;
        font-size: 2rem;
        line-height: 1;
        color: #9a9a9a;
    }
    #favoritos-carrusel img {
        width: 100%;
        height: auto;
        display: block;
        margin-top: .5rem;
    }
    #favoritos-carrusel h3 { margin: .75rem 0 .35rem; }
    #favoritos-carrusel time { display: block; margin: .5rem 0; font-size: .875rem; color: #5a5a5a; }
    #favoritos-carrusel:focus-visible { outline: 2px solid currentColor; outline-offset: 4px; }
    @media (prefers-reduced-motion: reduce) {
        #favoritos-carrusel { scroll-behavior: auto; }
    }
</style>


<!-- JavaScript: solo para los botones Anterior y Siguiente.
     Sin él, el carrusel se sigue navegando con el dedo, la rueda
     del ratón o las flechas del teclado. -->
<script>
    (function () {
        const carrusel = document.getElementById('favoritos-carrusel');
        const paso = () => carrusel.querySelector('li').offsetWidth + 24;

        document.querySelector('[data-favoritos-anterior]')
            .addEventListener('click', () => carrusel.scrollBy({ left: -paso() }));

        document.querySelector('[data-favoritos-siguiente]')
            .addEventListener('click', () => carrusel.scrollBy({ left: paso() }));
    })();
</script>
