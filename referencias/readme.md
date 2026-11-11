# Referencias Bibliográficas — Proyecto Beta: Selectividad del Receptor (Comunicaciones II)

Este repositorio contiene la implementación en GNU Radio Companion (GRC), modelos de simulación y evidencias experimentales con HackRF One para el análisis de **Selectividad del Receptor frente a Emisiones Cercanas (Escenario S6)**.

A continuación, se listan las referencias bibliográficas en formato IEEE organizadas formalmente según su aporte a la justificación del diseño técnico del sistema.

---

## 1. Selectividad y Mitigación de Interferencia de Canal Adyacente (ACI)

*Respaldan la elección del problema P1, la evaluación del impacto del interferente de banda estrecha ($f_{int}$) desplazado en frecuencia y el análisis de degradación de la BER/constelación ante solapamiento espectral.*

* [1] M. S. El-Tanany, S. A. Hanna, and G. K. Chan, "Adjacent channel selectivity for land mobile radio systems," in *Proc. IEEE 49th Vehicular Technology Conference (VTC)*, Houston, TX, USA, 1999, vol. 1, pp. 601–605, doi: [10.1109/VETEC.1999.778128](https://doi.org/10.1109/VETEC.1999.778128).
* [2] H. Gao, W. Liu, K. Wan, and J. Li, "On the impact of noise power estimation for soft information generation in OFDM-based PLC systems," in *Proc. IEEE Int. Symp. Power Line Commun. Appl. (ISPLC)*, Bottrop, Germany, 2016, pp. 64–69, doi: [10.1109/ISPLC.2016.7476271](https://doi.org/10.1109/ISPLC.2016.7476271).

---

## 2. Conformación de Pulso y Filtrado Acoplado (RRC)

*Justifican la elección del filtro de raíz de coseno alzado (RRC con factor de roll-off $\beta=0.35$) como filtro de canal en Tx/Rx para delimitación de banda útil y control del ancha de banda ocupado ($BW = R_s(1+\beta)$).*

* [3] M. Gupta and R. S. Gamad, "Symbol Error Rate Analysis of Generalized Frequency Division Multiplexing in Pulse Shaping Root Raised Cosine Filter," in *Proc. IEEE 11th Int. Conf. Commun. Syst. Netw. Technol. (CSNT)*, Indore, India, 2022, pp. 647–650, doi: [10.1109/CSNT54456.2022.9787565](https://doi.org/10.1109/CSNT54456.2022.9787565).

---

## 3. Arquitectura SDR y Validación Experimental (GNU Radio & Hardware)

*Respaldan la metodología de pruebas con plataformas de Radio Definida por Software (SDR), el flujo de datos en GNU Radio y la evaluación experimental en hardware.*

* [4] S. Aouthu *et al.*, "Digital Voice Transmission Using Software-Defined Radio," in *Proc. IEEE Wireless Antenna and Microwave Symposium (WAMS)*, Chennai, India, 2025, pp. 1–5, doi: [10.1109/WAMS64402.2025.11157936](https://doi.org/10.1109/WAMS64402.2025.11157936).
* [5] B. Adhikari, P. Jain, and Jamadagni H. S., "An ultra-wideband frequency Domain receiver for software defined radio applications," in *Proc. IEEE Int. Conf. Electron., Comput. Commun. Technol. (CONECCT)*, Bangalore, India, 2015, pp. 1–6, doi: [10.1109/CONECCT.2015.7383934](https://doi.org/10.1109/CONECCT.2015.7383934).

---

## 4. Procesamiento Digital de Señal y Modelado en Banda Base

*Justifican la elección de parámetros de sobremuestreo ($SPS=8$, $f_s=Rs \times SPS = 256 \text{ kS/s}$), el procesamiento en banda base compleja ($I/Q$) y la representación del espectro discreto.*

* [6] X. Wu, B. Jiang, and Q. Yin, "Software-defined radio based baseband discrete model for orthogonal frequency division multiplexing CDMA systems," in *Proc. IEEE VTS 53rd Vehicular Technology Conference (VTC Spring)*, Rhodes, Greece, 2001, vol. 2, pp. 771–775, doi: [10.1109/VETECS.2001.944483](https://doi.org/10.1109/VETECS.2001.944483).
* [7] M. Mishali, A. Elron, and Y. C. Eldar, "Sub-Nyquist processing with the modulated wideband converter," in *Proc. IEEE Int. Conf. Acoust., Speech, Signal Process. (ICASSP)*, Dallas, TX, USA, 2010, pp. 3626–3629, doi: [10.1109/ICASSP.2010.5495911](https://doi.org/10.1109/ICASSP.2010.5495911).
* [8] T. Long, F. Li, and D. Li, "A high-speed real-time digital signal processor for the modulated frequency stepped pulse radar signal," in *Proc. 5th Int. Conf. Signal Process. (ICOSP)*, Beijing, China, 2000, vol. 3, pp. 1847–1850, doi: [10.1109/ICOSP.2000.893462](https://doi.org/10.1109/ICOSP.2000.893462).