# Ficha Técnica de Producto — Silver Industrial

## Qué es
Catálogo visual de productos con ficha técnica por familia (nombre → variantes de
color/inserto), construido sobre el maestro real de Silver (1.867 familias / 1.978
códigos). Reemplaza la planilla Excel con hack de nombres definidos por una app
web simple.

## Cómo usarla
Abrí `index.html` en el navegador (funciona local o en GitHub Pages, no necesita
servidor ni base de datos). Subila a un repo y activá GitHub Pages, igual que
Planificador Silver y NC Silver.

## Qué trae cargado
- 1.867 familias de producto desde `Base de datos` (Base_y_Ficha_de_Producto.xlsm)
- 37 fotos reales de producto ya rescatadas y mapeadas
- 75 logos de cliente reales, resueltos para ~1.729 familias
- Resto de familias sin foto/logo: quedan con placeholder "sin foto" hasta que
  Mariano las cargue

## Qué falta (a propósito, para ir viendo con uso real)
- Los cambios de campo de la ficha (material, ciclo, descripción, altas rápidas)
  todavía quedan en el localStorage del navegador, no compartidos entre dispositivos.
- Sin validación de capacidad de pallet (a propósito, según lo definido)
- Molde real del grupo PUÑOS (308 BIS) ya resuelto: mismo número para molde y
  estantería, se carga tal cual

## Molde y ubicación (conectado al P.07)
Cada ficha tiene el bloque "Molde y ubicación · P.07", que lee EN VIVO del P.07 (Neon) a
través de un vínculo familia → molde. La ficha no guarda posiciones: el molde se mueve
solamente en el P.07 y la ficha lo refleja. Las tarjetas muestran la ubicación
("Ubic. 307 BIS"; punteada = vínculo sugerido sin confirmar).
- Se conecta con la misma clave y nombre que el P.07 (si ya entraste al P.07 desde el mismo
  navegador, entra solo). Clave de planta = solo lectura. Clave de administrador = vincular,
  confirmar y desvincular.
- `config.js` trae API_URL (Worker del P.07) y P07_URL.
- El campo viejo "Molde (dato de la planilla anterior)" se conserva como referencia.
- **Vincular por molde** (solo administrador, chip en el encabezado): elegís un molde del P.07
  (filtro "solo sin productos"), la pantalla propone productos probables (coincidencia de
  cliente +3, de nombre con la especificación +2), tildás y "Vincular marcados". Se puede quitar
  un vínculo desde la misma pantalla. Los vínculos sugeridos aparecen como "sugerido sin confirmar".
- Requiere haber corrido `vinculos.sql` en Neon (repo del API, carpeta db).

## Fotos, edición y control de cambios (compartidos)
Todo se guarda en Neon a través del Worker del P.07 y lo ven todos los dispositivos.
- **Clave de planta:** ve ubicaciones, sube fotos de producto y da de alta fichas nuevas.
- **Clave de administrador:** además edita todos los campos, el logo del cliente y los vínculos con moldes.
- **Sin conexión:** solo lectura del maestro.
- Cada edición queda en el **control de cambios** de la ficha (campo, antes, después, quién, cuándo).
- Si el navegador tenía ediciones guardadas de la versión anterior, el administrador ve el botón "Subir N cambio(s) locales".
Requiere correr en Neon: `vinculos.sql`, `fotos.sql` y `ficha_datos.sql` (repo del API, carpeta db).

## Imprimir la ficha (Q.12)
Botón "Imprimir ficha (Q.12)" en cada ficha: arma una hoja A4 con encabezado Silver (REV 03, COD Q.12), datos del producto, foto y logo, molde y ubicación vigente del P.07 (más otros productos que comparten el molde), requisitos del cliente, controles, descripción y control de cambios.

## Edición
Los campos se editan con un click (solo administrador). El maestro original (`data.js`) no se
toca: en Neon se guarda únicamente el valor editado, y el control de cambios guarda el anterior.

## Alta rápida
Botón "+ Alta rápida" en el header: pensado para que Fernando pueda crear una
ficha nueva en el momento (al ofrecer el servicio a otra empresa), cargando
solo nombre + cliente + material. El resto (foto, medidas, dosificación,
molde) se completa después desde la ficha misma. Igual que el resto de la
edición, estas fichas nuevas hoy quedan en el localStorage del navegador — no
se comparten entre dispositivos todavía.
