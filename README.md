
*** PREDIX DOLAR v2.0 - SISTEMA INTELIGENTE DE PREDICCION USD/COP ***

DESCRIPCION GENERAL:
PredixDolar es un ecosistema multi-agente de Inteligencia Artificial 
especializado en el par USD/COP (Dolar vs Peso Colombiano). El sistema 
utiliza un diseño de grafo (LangGraph) para coordinar multiples agentes 
expertos que analizan el mercado desde diferentes angulos.

EL PROTOCOLO DE TRIPLE SEÑAL:
El corazon de la version 2.0 es su metodo de decision desglosado:

1. SEÑAL TECNICA: 
   - Modelo ARIMA (AutoR) para pronostico puntual de cierre.
   - Simulacion Monte Carlo de 50,000 escenarios centrada en ARIMA.
   
2. SEÑAL FUNDAMENTAL:
   - Analisis de noticias en tiempo real con Tavily.
   - Scoring de sentimiento (-1 a +1) mediante IA (modelo IA local - Qwen2.5).

3. SEÑAL DE TENDENCIA:
   - Calculo de Medias Moviles (MA) de 90 y 180 dias.
   - Actua como un filtro de realidad para evitar falsas señales.

EL CEREBRO (AGENTE DIRECTOR):
El Director recibe los reportes de las tres señales y aplica una logica
de confianza:
- 3/3 señales alineadas: Confianza ALTA.
- 2/3 señales alineadas: Confianza MEDIA.
- 1/3 o señales mixtas: Confianza BAJA (Recomienda ESPERAR).

MEMORIA Y APRENDIZAJE (REINFORCEMENT LEARNING):
El sistema no solo predice, sino que aprende. Cada dia, un agente 
"Critico" evalua el acierto del dia anterior. Si hubo un error, analiza 
especificamente cual de las tres señales fallo y guarda una leccion 
en la base de datos SQLite para que el Director la tome en cuenta mañana.

INTERFAZ DE TELEGRAM:
El bot permite interactuar mediante comandos:
- /analisis: Ejecuta el flujo completo Triple Señal.
- /prediccion: Muestra el pronostico tecnico ARIMA.
- /tendencia: Muestra el estado de las medias moviles.
- /montecarlo: Muestra la campana de Gauss de probabilidades.
- /menu: Muestra el panel principal.

INFRAESTRUCTURA:
Optimizado para correr 24/7 en una Raspberry Pi 5, utilizando un 
servicio de sistema (systemd) para asegurar la maxima estabilidad.

*** Desarrollado con Python, LangGraph, Google Gemini & modelo local Qwen2.5 ***

Oscar J Carabali P. - 2026
