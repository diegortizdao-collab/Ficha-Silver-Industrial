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
- Carga de foto por variante (Mariano, en máquina) — el botón está pensado pero
  el flujo de subida de imagen desde el navegador todavía no está conectado a
  ningún backend; hoy los cambios de campo quedan en localStorage del navegador,
  no compartidos entre dispositivos (mismo punto de partida que tuvo el
  Planificador antes de migrar a Firebase)
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
- Requiere haber corrido `vinculos.sql` en Neon (repo del API, carpeta db).

## Edición
Cualquier campo de la ficha técnica es editable con un click (igual que el
maestro del Planificador). Los cambios sobrescriben el dato original del Excel
sin perderlo (el archivo base no se toca, solo se guarda el override).

## Alta rápida
Botón "+ Alta rápida" en el header: pensado para que Fernando pueda crear una
ficha nueva en el momento (al ofrecer el servicio a otra empresa), cargando
solo nombre + cliente + material. El resto (foto, medidas, dosificación,
molde) se completa después desde la ficha misma. Igual que el resto de la
edición, estas fichas nuevas hoy quedan en el localStorage del navegador — no
se comparten entre dispositivos todavía.
