# Product backlog — Liga de básquetbol

## Contexto
Aplicación académica. Se priorizan funcionalidades que aportan utilidad al usuario y se estiman con tamaños relativos de **1 o 2 puntos**, como solicita la práctica. Valor: 1 (bajo), 2 (medio), 3 (alto). La estimación es inicial y debe validarse en una reunión del equipo.

| Prioridad | Historia | Tamaño | Valor | Estado |
| --- | --- | ---: | ---: | --- |
| 1 | HU-01 Registrar equipos | 1 | 3 | Implementación inicial en feature/gestion-liga |
| 2 | HU-02 Programar partidos | 2 | 3 | Implementación inicial en feature/gestion-liga |
| 3 | HU-03 Registrar resultados y clasificación | 2 | 3 | Implementación inicial en feature/gestion-liga |
| 4 | HU-04 Filtrar partidos por equipo | 1 | 2 | Backlog próxima iteración |
| 5 | HU-05 Exportar clasificación a CSV | 1 | 2 | Backlog próxima iteración |
| 6 | HU-06 Validar fechas y evitar choques horarios | 2 | 3 | Backlog próxima iteración |

## HU-01: Registrar equipos
**Historia:** Como organizador quiero registrar el nombre, entrenador y ciudad de un equipo para mantener la lista de participantes.

**Boceto**
```text
[ Equipos ]
Nombre: [______________] Entrenador: [____________]
Ciudad: [______________] [ Agregar equipo ]
----------------------------------------------------
Equipo              Entrenador           Acción
Cóndores            Ana Pérez            Eliminar
```
**Condiciones de satisfacción:** se exigen los tres campos; no se permiten nombres de equipo repetidos ignorando mayúsculas; el equipo aparece en el listado; se conserva al recargar.

## HU-02: Programar partidos
**Historia:** Como organizador quiero programar enfrentamientos entre dos equipos para publicar los próximos encuentros.

**Boceto**
```text
[ Partidos ]
Local: [ seleccionar ] Visitante: [ seleccionar ]
Fecha y hora: [ yyyy-mm-dd hh:mm ] [ Programar ]
```
**Condiciones:** ambos equipos deben existir; el local y visitante son diferentes; la fecha es obligatoria; aparece el encuentro programado.

## HU-03: Registrar resultados y consultar clasificación
**Historia:** Como organizador quiero ingresar el marcador final de un partido para actualizar la clasificación.

**Boceto**
```text
Equipo           PJ   PG   PP    PF    PC   Puntos
Cóndores          2    2    0   130   112     4
```
**Condiciones:** los marcadores son enteros no negativos; no se aceptan empates; se suman las estadísticas; el orden se define por puntos, diferencia y puntos a favor.

## HU-04: Filtrar partidos por equipo
**Historia:** Como aficionado quiero filtrar los encuentros de mi equipo para ver solo sus partidos.
**Boceto:** `Equipo [Seleccionar ▼] [Filtrar]`
**Condiciones:** se muestran solo los encuentros del equipo seleccionado; existe la opción Todos.

## HU-05: Exportar clasificación a CSV
**Historia:** Como organizador quiero descargar la tabla de posiciones para compartirla con los equipos.
**Boceto:** `[ Descargar CSV ]`
**Condiciones:** el archivo incluye los encabezados y la clasificación actual; se abre con una hoja de cálculo.

## HU-06: Evitar choques horarios
**Historia:** Como organizador quiero recibir una advertencia cuando un equipo tenga dos partidos a la misma hora para evitar conflictos.
**Boceto:** `Aviso: El equipo ya tiene un partido en esa fecha y hora.`
**Condiciones:** no se puede guardar un segundo encuentro con coincidencia exacta de equipo y fecha/hora; se indica el conflicto.

## Flujo de GitHub
Crear un issue por historia, asignar responsable, poner el issue en el tablero del proyecto, crear una rama `feature/*`, subir commits y abrir un PR hacia `develop`. Otro integrante debe revisar y aprobar el PR antes de integrarlo. La revisión no se sustituye por una aprobación ficticia.

## Pruebas manuales iniciales
1. Registrar dos equipos, y verificar que se listan y persisten tras recargar.
2. Intentar registrar un nombre repetido: se rechaza.
3. Intentar enfrentar un equipo consigo mismo: se rechaza.
4. Programar encuentro con equipos distintos y fecha válida.
5. Registrar marcador 50-40 y comprobar clasificación (ganador: 2 puntos; perdedor: 1).
6. Intentar marcador empatado: se rechaza.
7. Eliminar un equipo con encuentros vinculados: el sistema debe impedirlo.
