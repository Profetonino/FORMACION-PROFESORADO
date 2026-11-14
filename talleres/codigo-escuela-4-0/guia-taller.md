# Sesión 2 · Del sensor a la acción

**Micro:bit V2, Maqueen Plus V2 y ESP32 ACEBOTT**  
CEP Bollullos/Valverde · Código Escuela 4.0  
Docente: Juan Antonio Pérez Rodríguez · ProfeTonino  
Actualización: 12/11/2026

## Propósito y destinatarios

El profesorado participante ya conoce micro:bit. La primera parte es un repaso práctico: leer una entrada, interpretar un dato y producir una respuesta. Después se aplica la misma idea al robot Maqueen y a la placa ESP32 Plus. Las propuestas de micro:bit y Maqueen incluyen Primaria y Secundaria; ACEBOTT corresponde a Secundaria.

El objetivo es abrir proyectos preparados, explicar su lógica, modificar un parámetro con una intención y llevar una propuesta concreta al aula. La sesión no exige escribir todos los programas desde cero.

## Organización de los 220 minutos efectivos

| Parte | Duración | Acumulado |
|---|---:|---:|
| Presentación y rutina de trabajo | 10 min | 10 min |
| Micro:bit V2 | 65 min | 75 min |
| Cambio de material | 5 min | 80 min |
| Maqueen Plus V2 | 55 min | 135 min |
| Cambio de material | 5 min | 140 min |
| ESP32 Plus y ACECode | 65 min | 205 min |
| Puesta en común y transferencia al aula | 15 min | 220 min |

El descanso de la convocatoria se sitúa fuera de estos 220 minutos. Las propuestas de aula tienen sus propias duraciones: no se realizan completas durante el taller.

Trabajo en parejas; en tríos, se añade el papel de registro. Una persona programa, otra observa y comprueba. Se intercambian los papeles al cambiar de práctica. Antes de cargar, se anticipa el resultado; después se modifica una sola cosa y se compara.

## Materiales y archivos

- Ordenador, navegador y conexión para abrir los proyectos públicos de MakeCode y descargar los archivos de Drive.
- Micro:bit V2, cable USB de datos, expansión, servo y sensor infrarrojo del montaje P0/P6.
- Maqueen Plus V2 montado y su alimentación. Circuito de cinta negra sobre fondo claro y obstáculo ancho para el ultrasonido.
- ESP32 Plus y shield 9 en 1 para los primeros ejemplos. DHT11 externo y LCD 1602 con adaptador I²C para la estación; cables adecuados a las etiquetas de cada módulo.
- Regla o cinta métrica, marcas de salida, hojas de registro y materiales ligeros de maqueta.

El archivo principal es `Taller-materiales-escuela-4.0.html`. Contiene estilos, imágenes y funciones; basta compartir ese archivo para abrir el material. Cada práctica enlaza su proyecto. MakeCode ofrece copias editables y descarga .hex; ACECode usa proyectos .sb3 descargados de Drive. Guardar un proyecto no equivale a cargarlo en la placa.

## Micro:bit V2 · 65 minutos

| Práctica | Tiempo | Idea central |
|---|---:|---|
| Luz y decisiones | 10 min | Lectura relativa 0–255, umbral 80 y dos iconos |
| Una barra que escucha | 10 min | Nivel de sonido relativo y escala del gráfico |
| Servo con A/B | 20 min | Eventos, dos posiciones y control desde Pines sin extensión adicional |
| Barrera con infrarrojo | 25 min | Entrada digital P6, condición y servo P0 |

La luz y el sonido integrados no se presentan como medidas calibradas en lux o decibelios. En el servo, 0° y 90° son órdenes: abierto y cerrado dependen de la mecánica. La barrera automática conserva la extensión Servos de su proyecto.

En la barrera se deshabilita la matriz con «activar LED = falso» porque P6 es compartido. Bajar el brillo a cero o borrar un icono no libera ese pin. Se distingue señal, alimentación y masa; se sigue la infografía de cada montaje. Las conexiones se cambian con la alimentación desconectada.

La web desarrolla propuestas de aula con objetivo, preparación, pasos, producto y evaluación. En Primaria se priorizan predicciones y explicaciones con maquetas; en Secundaria se añade documentación de condiciones, parámetros y resultados.

## Maqueen Plus V2 · 55 minutos

| Parte | Tiempo | Programa y observación |
|---|---:|---|
| Reconocer y preparar el robot | 5 min | Componentes, alimentación e inicialización |
| Movimiento y luces | 10 min | Azul preparado; A inicia un avance de 1 s a 80 con verde y luces; al terminar muestra rojo; B detiene |
| Obstáculos | 15 min | Primero mostrar distancia con el robot parado; después avanzar y detener ante lectura 0 o menor que 30 cm |
| Sigue líneas | 20 min | Base con recta 100 y correcciones 160/30; comparar ajustes |
| Cierre del bloque | 5 min | Explicar una decisión y una mejora apoyada en observaciones |

Las consignas de motor no expresan cm/s. La pausa mantiene una orden anterior; no detiene el motor por sí sola. En el programa de distancia, el desplazamiento del número por la matriz también consume tiempo: no se promete una lectura exactamente cada 200 ms.

En el sigue líneas se comprueba primero el sensor central M. Si M detecta negro, ambos motores avanzan. Con M en blanco se aplican las correcciones L1/R1 previstas. Ante otro patrón, se detienen los motores y se desactiva enMarcha. Hace falta pulsar A para reiniciar. La base ya incluye esa parada; no se propone añadirla como si faltara.

La copia con valores 100/120/60 utiliza la misma lógica que la base. Reduce la diferencia entre ruedas; puede reducir oscilaciones, pero su resultado depende del circuito. Se compara con la base manteniendo trazado, robot y salida. El control proporcional es una ampliación posterior, no el nombre de estas dos velocidades fijas.

## ESP32 Plus y ACECode · 65 minutos

| Parte | Tiempo | Contenido |
|---|---:|---|
| Placa, editor, archivos y primer parpadeo | 15 min | ESP32, Modo de carga, apertura y guardado de .sb3, firmware frente a programa |
| Botón y luces | 10 min | SW1 controla el LED rojo; comparar extensión y GPIO |
| Sensores por puerto serie | 20 min | Potenciómetro, LDR y LM35, con sus escalas y unidades |
| Estación ambiental | 20 min | DHT11 externo y LCD 1602 I²C; lectura y ampliación con aviso |

Se utiliza ACECode Online en modo de carga, con Python generado por los bloques. La extensión 9 in 1 Easy Module Shield V1 reconoce los componentes integrados. La versión por GPIO hace explícita la correspondencia entre la serigrafía y el número de pin. No se mezclan ambas versiones dentro de un mismo ejemplo.

En el potenciómetro, el mapeo proporcional cambia la escala de entrada a 0–255 para el brillo. Redondear solo convierte el resultado final en entero. La LDR aporta un dato relativo, no lux; su umbral se elige a partir de observaciones. La estimación del LM35 por GPIO usa la configuración ADC que genera ese bloque y no se presenta como una medida calibrada.

### Estación ambiental

- DHT11 externo: señal en GPIO27. Los dos bloques Humedad temperatura seleccionan ese pin.
- LCD 1602 I²C: SDA en GPIO21, SCL en GPIO22 y dirección 0x27 en el módulo del montaje. Se respetan GND/G y VCC/V según la infografía.
- La LCD dispone de 16 columnas y dos filas: x = 0–15 e y = 0–1. La numeración comienza en cero.
- La práctica básica conserva el texto de las lecturas, incluidos los decimales que entregue el lector, y lo presenta con etiquetas y unidades. No redondea ni convierte a entero para mostrarlo.
- La ampliación conserva la misma presentación. Solo aplica Convertir a entero dentro de una decisión con umbral entero positivo y comparador ≥. Con umbral 28: 27,9 no activa ALTA; 28 y 28,7 sí. La igualdad activa el aviso. Esta regla no está diseñada para umbrales decimales.
- Convertir a entero trunca la parte decimal. El bloque Configurar tipo de datos → Número flotante no añadió una conversión en la inspección de Python; no se utiliza como solución de conversión decimal.

La infografía se abre con ampliación y zoom. Sus cifras son ilustrativas. La propuesta de aula compara dos zonas mediante varias medidas y una recomendación razonada; temperatura y humedad por sí solas no certifican confort ni calidad del aire.

## Cierre y transferencia · 15 minutos

Cada pareja elige una actividad para su etapa y concreta: qué aprenderá el alumnado, qué material necesita, qué producto entregará y qué observación permitirá valorar el aprendizaje. Comparte una modificación del programa y explica su efecto con los datos de sus ensayos.

Para revisar un programa se comprueba la correspondencia entre entrada, condición y salida; los pines; el tratamiento del dato; las unidades; las pausas; y el comportamiento en ambos casos de una decisión. Una captura debe coincidir con el archivo y con su explicación.
