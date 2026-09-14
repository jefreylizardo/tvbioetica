# tvbioetica.com

Código fuente de **Tertulia Virtual de Bioética**, periódico digital semanal sobre
bioética, ética en salud, equidad, derechos humanos y ética de la tecnología.
Cierre de edición: domingo por la noche.

X e Instagram: [@TVbioetica](https://x.com/TVbioetica)

---

## Qué hay aquí

```
index.html                    la edición actual — es lo único que cambia cada semana
ediciones/index.html          archivo histórico (añadir un <li> por edición)
ediciones/2026-09-13-...html  copia congelada de cada edición publicada
og.png                        imagen que aparece al compartir el enlace
favicon-32 / 180 / 512.png    iconos del sitio
logo.svg                      logo vectorial
GUIA-ACTUALIZACION.md         cómo se estructura el contenido
```

Todo el contenido del periódico vive en un único objeto `EDICION` dentro de
`index.html`. El diseño, los filtros y el modo noche no se tocan nunca.

---

## Publicar una edición nueva

El domingo, en cuatro pasos, todo desde el navegador:

**1. Congelar la edición que sale de portada.**
En `ediciones/`, use *Add file → Upload files* y suba una copia del `index.html`
actual con el nombre `AAAA-MM-DD-edicion-NN.html`.

**2. Añadirla al archivo.**
Abra `ediciones/index.html`, pulse el lápiz, copie el bloque `<li>` de la edición
anterior y péguelo arriba con el número, la fecha, el enlace y el titular nuevos.

**3. Reemplazar la portada.**
Abra `index.html`, pulse el lápiz, busque `const EDICION = {` y sustituya el objeto
completo por el de la semana. Confirme con *Commit changes*.

**4. Verificar.**
Porkbun sincroniza en uno o dos minutos. Abra tvbioetica.com y recargue forzando
caché (Ctrl+F5, o Cmd+Shift+R en Mac).

Si algo sale mal, la pestaña *Commits* guarda todas las versiones anteriores:
entre al commit bueno, abra el archivo y use *Revert*. Nunca se pierde una edición.

---

## Despliegue

El repositorio está conectado a **Porkbun Static Hosting** mediante GitHub Connect.
Cada `commit` a la rama principal se publica solo. No hay que subir nada por FTP.

Alternativa sin costo de hosting: GitHub Pages sirve este mismo repositorio tal cual
—apuntando los registros A del dominio a GitHub y añadiendo un archivo `CNAME` con
`tvbioetica.com`—. Solo tiene sentido si prefiere no pagar el plan de Porkbun.

---

## Criterios editoriales

1. Cada nota enlaza su fuente primaria.
2. Cuando un hecho está en disputa entre fuentes, se dice en el texto.
3. Las opiniones firmadas no comprometen a las instituciones de sus autores.
4. El contrapunto no se cierra: se exponen las dos posiciones y decide quien lee.
