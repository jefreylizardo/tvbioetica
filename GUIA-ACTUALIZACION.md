# TvBioética — guía de actualización semanal

## Lo primero

Todo el contenido del periódico vive en **un solo objeto** dentro de `tvbioetica.html`.
Busque en el archivo la línea que dice `const EDICION = {` y reemplace ese objeto
completo (hasta el `};` que lo cierra) por el de la semana nueva. El diseño, los
filtros, el modo noche y los enlaces a redes no se tocan nunca.

Publicar es subir el archivo. Sirve cualquier alojamiento estático: GitHub Pages,
Netlify, Cloudflare Pages, Vercel o la carpeta pública de un hosting tradicional.

---

## El prompt de cada domingo

Péguelo tal cual en una conversación nueva conmigo, adjuntando `tvbioetica.html`:

> Prepara la edición número **[N]** de TvBioética, con fecha **[domingo]**.
> Busca en la web las noticias y publicaciones de la última semana sobre bioética,
> ética en salud, dignidad humana, justicia social, ética de la IA y de la tecnología,
> derechos humanos, equidad y determinantes sociales de la salud, con atención a
> América Latina y el Caribe. Devuélveme el objeto `EDICION` completo, listo para
> pegar, respetando la estructura del archivo adjunto: pregunta de la semana,
> 4 puntos en "lo esencial", portada con recuadro de 3 preguntas, entre 8 y 12 notas
> con fuentes enlazadas, un contrapunto con dos posiciones, un artículo de reflexión
> de unas 800 palabras, concepto de la semana, "en el radar" y 6 lecturas.
> Cada nota debe enlazar su fuente primaria. Si un hecho está en disputa entre
> fuentes, dilo en el texto en lugar de elegir una versión.

Si prefiere que le entregue el archivo entero ya actualizado, pídalo así y lo devuelvo
listo para subir.

---

## Estructura del objeto `EDICION`

| Campo | Qué es |
|---|---|
| `numero`, `fecha`, `proxima`, `correo` | Datos de cabecera y pie |
| `pregunta`, `preguntaBajada`, `preguntaFirma` | La apertura. Es una pregunta, no un titular |
| `esencial` | 4 entradas de `{titulo, texto}` |
| `portada` | `{seccion, titulo, sumario, cuerpo:[], fuentes:[{nombre,url}]}` |
| `aparte` | Recuadro de la portada: `{titulo, puntos:[]}` |
| `articulos` | Las notas. Cada una: `{seccion, lugar, titulo, sumario, texto:[], fuentes:[]}` |
| `contrapunto` | `{tema, intro, a:{titulo,cuerpo:[]}, b:{titulo,cuerpo:[]}, cierre}` |
| `ensayo` | `{titulo, bajada, cuerpo:[], firma}` |
| `concepto` | `{termino, definicion, porque}` |
| `radar` | `{cuando, titulo, detalle}` |
| `lecturas` | `{titulo, autor, donde, url, nota}` |

Los filtros de sección se generan solos a partir del campo `seccion` de cada nota.
Si inventa una sección nueva, aparece sola en la barra. Si una semana no hay notas
de una sección, esa sección simplemente no se muestra.

**Secciones en uso:** Justicia social y financiamiento · Genómica y biotecnología ·
Ética de la inteligencia artificial · Bioética clínica y final de la vida ·
Ética de la investigación · Equidad y determinantes sociales ·
América Latina y el Caribe · Derechos humanos y dignidad.

---

## Criterios editoriales de la cabecera

Están escritos en el pie del sitio y conviene sostenerlos:

1. Cada nota enlaza su fuente primaria.
2. Cuando un hecho está en disputa entre fuentes, se dice en el texto.
3. Las opiniones firmadas no comprometen a las instituciones de sus autores.

Un cuarto criterio, implícito en el diseño: el contrapunto nunca se cierra. El sitio
plantea las dos posiciones y deja la decisión al lector. Es lo que distingue una
tertulia de un editorial.

---

## Sobre el logo

El logo es un SVG dibujado dentro del HTML, sin archivos externos: una casa cuyo suelo
es un latido, con una hoja creciendo dentro. Casa común, vida que se cuida, personas
que la habitan. No hay rostro ni figuras humanas, para no sugerir un tipo de persona
sobre otro. El verde de marca es `#10AF58` y el verde profundo `#08633A`. Para cambiarlo, edite las variables `--verde` y
`--verde-hondo` al inicio del `<style>`; todo el sitio se actualiza.

En el pie, sobre fondo oscuro, el verde profundo se sustituye automáticamente por un
tono claro mediante la variable `--logo-oscuro`. Si cambia los verdes, revise también
esa regla.

Para redes sociales se incluye `logo-tvbioetica.svg`, listo para exportar a PNG de
1000×1000 como avatar de X e Instagram.

---

## Automatizar el domingo por la noche

Yo no me ejecuto solo: la edición se genera cuando usted la pide. Para que ocurra sin
depender de la memoria, tiene dos caminos:

- **Recordatorio.** Un aviso recurrente los domingos a las 7:00 p. m. con el prompt de
  arriba guardado en la nota. Es el camino más simple y lo más parecido a una redacción.
- **Automatización propia.** Un script que llame a la API de Anthropic cada domingo,
  reciba el objeto `EDICION` en JSON, lo inyecte en el HTML y publique por FTP o
  `git push`. Requiere una clave de API y un servidor o un runner de GitHub Actions.

Si quiere el segundo camino, pídamelo y le escribo el script y el flujo de despliegue.
