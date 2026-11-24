# TRADING PRO para Android y ordenador

## Qué incluye
- Aplicación web instalable (PWA), diseño oscuro adaptable.
- Análisis local de CSV diario con RSI(14), EMA 20/50, MACD y ATR.
- Señales educativas COMPRAR / VENDER / MANTENER.
- Cálculo orientativo de stop, objetivo y tamaño de posición con capital de referencia de 1.000 €.
- Lista de seguimiento guardada en el dispositivo.
- Notificación local al detectar un cambio de señal mientras la aplicación está abierta.

## Cómo usar
1. Descomprime el ZIP.
2. Sirve la carpeta desde un alojamiento HTTPS o servidor local. Para probar en ordenador:
   `python -m http.server 8000`
   y abre `http://localhost:8000`.
3. En Android, abre la dirección HTTPS en Chrome y usa menú ⋮ > **Instalar aplicación** o **Añadir a pantalla de inicio**.
4. Permite notificaciones si quieres avisos mientras la app está abierta.
5. Exporta datos históricos diarios en CSV con columnas `Date, Open, High, Low, Close, Volume` e impórtalos.

## Limitaciones importantes
- No descarga cotizaciones automáticamente ni es un servicio de datos en tiempo real.
- Las notificaciones son locales y no llegan si el navegador/app está cerrado o el dispositivo no ejecuta la app. Las notificaciones push 24/7 requieren alojamiento HTTPS y un backend de push.
- No envía órdenes a bróker ni compra/vende activos.
- En acciones estadounidenses, el cálculo se muestra en USD si se elige USD, pero el presupuesto está expresado en EUR. Convierte el capital y contempla cambio y comisiones antes de usar el tamaño de posición.
- El CSV debe estar en formato estándar separado por comas, con una fila por sesión y datos ordenados de más antiguo a más reciente.
- Los datos históricos y las señales no predicen el futuro. Usa primero una cuenta demo.

## Parámetros de la estrategia
Compra: precio > EMA50, EMA20 > EMA50, MACD > línea de señal y RSI entre 45 y 68.
Venta: precio < EMA50 y EMA20 < EMA50, o cruce bajista MACD con RSI >= 50.
Stop orientativo: cierre - 2 × ATR(14). Objetivo: cierre + 4 × ATR(14).
Riesgo presupuestado: 1% del capital. Límite de inversión por valor: 20%.
