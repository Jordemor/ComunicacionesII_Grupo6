# Proyecto Integrador: Selectividad del Receptor frente a una Emisión Cercana (Escenario S6)

🌐 **Enlace al Blog del Proyecto (Divulgación Técnica ABET):** [https://lambent-bonbon-4c2ae0.netlify.app/]  
📅 **Última actualización:** Noviembre de 2026  

---

## 📋 Integrantes del Grupo 6
* **Jordi Alberto Delgado Abril** (Código: 2230395)
* **María José Mosquera Gutiérrez** (Código: 2231775)
* **Daniel Santiago Rodríguez Arévalo** (Código: 2202325)
* **Valentina Afanador Afanador** (Código: 2230385)

**Institución:** Universidad Industrial de Santander (UIS)  
**Escuela:** Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones (E3T)
**Asignatura:** Comunicaciones II (Grupo 6)

---

## 📝 Resumen del Proyecto
Este repositorio documenta el desarrollo y validación experimental del **Escenario S6: Selectividad del receptor frente a una emisión cercana**, en el marco del Proyecto Integrador de Comunicaciones II. El sistema aborda el fenómeno físico del solapamiento espectral y la degradación de la selectividad en receptores digitales cuando un tono interferente de banda estrecha se aproxima a la banda útil. Se diseñó y simuló una arquitectura en GNU Radio Companion (GRC) comparando modulaciones QPSK y 16QAM bajo una tasa de símbolos constante ($R_s = 32\text{ ksym/s}$), aplicando conformación de pulso Raíz de Coseno Alzado (RRC con $\beta = 0.35$) y evaluando el desempeño mediante densidades espectrales de potencia (PSD), constelaciones, diagramas de ojo y métricas de tasa de error de bit (BER) y magnitud del vector de error (EVM). Los resultados de simulación fueron contrastados mediante una implementación física utilizando plataformas de Radio Definida por Software (SDR) con dispositivos HackRF One a 960 MHz.

---

## ⚙️ Parámetros Base del Sistema
* **Modulación Principal:** QPSK vs. 16QAM (misma tasa de símbolos para estudio de capacidad vs. robustez)
* **Tasa de Símbolos ($R_s$):** $32\text{ ksym/s}$
* **Tasa de Bits ($R_b$):** $64\text{ kbit/s}$ (QPSK) / $128\text{ kbit/s}$ (16QAM)
* **Muestras por Símbolo ($SPS$):** $8$ muestras/símbolo
* **Frecuencia de Muestreo ($f_s$):** $256\text{ kS/s}$ ($f_s = R_s \times SPS$)
* **Conformación de Pulso:** Raíz de Coseno Alzado (RRC) con factor de roll-off $\beta = 0.35$ en transmisor y receptor (filtro acoplado)
* **Ancho de Banda Útil ($BW$):** $43.2\text{ kHz}$ [$BW = R_s(1+\beta)$]
* **Perturbación:** Tono complejo interferente con frecuencia variable ($f_{int}$) y amplitud fija ($A_{int} = 0.5$)

---

## 🛠️ Archivos GRC y Estructura del Repositorio
Los flujogramas principales optimizados y ejecutables se encuentran en la carpeta `grc/`:
1. `LAB_TX_16QAM_HackRF_MEJORADO.grc`: Flujograma transmisor para pruebas en hardware SDR.
2. `LAB_RX_16QAM_HackRF_MEJORADO.grc`: Flujograma receptor con sincronización, filtrado RRC, cálculo de BER/EVM y decodificación de tramas

### Ejecución
Para ejecutar las simulaciones:
1. Abra el gestor de GNU Radio Companion en su entorno Ubuntu/WSL.
2. Cargue el archivo GRC deseado ubicado en la ruta `grc/`.
3. Verifique que las variables globales ($f_s$, $SPS$, $R_s$) coincidan con los parámetros base documentados.

---

## 📊 Plan Mínimo de Experimentación y Pruebas
Se implementó un plan de pruebas progresivo evaluando el comportamiento del receptor ante cuatro niveles de severidad del interferente:

| Prueba | Severidad | Frecuencia del Interferente ($f_{int}$) | Banda de Guarda ($\Delta f_g$) | Región del Filtro RRC | Efecto Observado / Comportamiento |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **A** | Referencia | Sin tono ($A_{int} = 0$) | N/A | N/A | Constelación limpia, $BER \approx 0$, sin solapamiento. |
| **B** | Suave | $48\text{ kHz}$ | $+26.4\text{ kHz}$ | Fuera de banda | Atenuación alta del filtro; sin impacto visible en la constelación. |
| **C** | Medio | $20\text{ kHz}$ | $-1.6\text{ kHz}$ | Zona de transición | Deformación leve de símbolos (anillos pequeños); umbral crítico para 16QAM. |
| **D** | Fuerte | $8\text{ kHz}$ | $-13.6\text{ kHz}$ | Zona plana | Solapamiento severo, cierre de ojo, aumento drástico de BER en 16QAM. |

*(Los registros detallados de métricas y datos numéricos crudos se encuentran disponibles en la carpeta `data/` del repositorio).*

---

## 🖼️ Representación Visual del Escenario
A continuación se muestra el contexto físico y el esquema de propagación del escenario S6 (ubicado en la carpeta `figures/`):

---

## 💡 Conclusiones Principales
1. **Selectividad y Filtrado:** El uso de filtros acoplados RRC con $\beta = 0.35$ garantiza una delimitación precisa del canal ($\pm 21.6\text{ kHz}$), proporcionando un rechazo superior a $40\text{ dB}$ fuera de banda para atenuar emisiones adyacentes.
2. **Sensibilidad de Modulación:** Al mantener la misma tasa de símbolos, se comprobó experimental y teóricamente que 16QAM requiere una relación señal a interferencia (SIR) estricta (~$10\text{ dB}$) en comparación con QPSK (~$3\text{ dB}$), volviéndose significativamente más vulnerable ante interferencias en la zona de transición.
3. **Validación Práctica:** Las pruebas con hardware HackRF One confirmaron que cuando la potencia de la señal útil decae frente a emisiones vecinas a $\pm 200\text{ kHz}$, la selectividad del receptor define la pérdida total o la recuperación exitosa del enlace (respaldado por métricas de $BER$, $EVM$ y $CRC$).

---

## 📚 Referencias Bibliográficas Principales
* [1] M. S. El-Tanany, S. A. Hanna, and G. K. Chan, "Adjacent channel selectivity for land mobile radio systems," in *Proc. IEEE 49th Vehicular Technology Conference (VTC)*, Houston, TX, USA, 1999, vol. 1, pp. 601–605.
* [2] M. Gupta and R. S. Gamad, "Symbol Error Rate Analysis of Generalized Frequency Division Multiplexing in Pulse Shaping Root Raised Cosine Filter," in *Proc. IEEE 11th Int. Conf. Commun. Syst. Netw. Technol. (CSNT)*, 2022, pp. 647–650.
* [3] S. Aouthu *et al.*, "Digital Voice Transmission Using Software-Defined Radio," in *Proc. IEEE Wireless Antenna and Microwave Symposium (WAMS)*, 2025, pp. 1–5.# ComunicacionesII_Grupo6
Repositorio oficial para la materia de comunicaciones II
