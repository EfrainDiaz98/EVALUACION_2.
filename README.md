# Evaluación 2 - Seguridad de la Información 🛡️
**Estudiante:** Efrain Yair Diaz Anzola  
**Institución:** Fundación Universitaria Compensar[cite: 1]  
**Facultad:** Ingeniería de Telecomunicaciones[cite: 1]

---

## 1. Parte Conceptual 📚

### A. Reconocimiento en Footprinting
* **Reconocimiento Pasivo:** Se realiza sin interactuar directamente con el objetivo (ej. búsquedas en WHOIS, redes sociales o Shodan)[cite: 1].
* **Reconocimiento Activo:** Implica interacción directa con el sistema para obtener datos precisos (ej. escaneo de puertos con Nmap o banners grabbing)[cite: 1].

### B. Exploits, Payloads y Post-Exploits
* **Exploit:** Código que aprovecha una vulnerabilidad para ganar acceso[cite: 1].
* **Payload:** La carga útil que ejecuta la acción deseada tras la explotación (ej. una reverse shell)[cite: 1].
* **Post-Exploit:** Acciones realizadas tras el compromiso inicial para mantener persistencia o elevar privilegios[cite: 1].

**Ejemplos:**
1. **Exploit:** EternalBlue (MS17-010) aprovechando vulnerabilidades en SMB[cite: 1].
2. **Payload:** Meterpreter, que permite control total del sistema comprometido en memoria[cite: 1].

### C. Metasploit en Entornos Reales
**Metasploit** sirve como un framework de pruebas de penetración para descubrir, explotar y validar vulnerabilidades[cite: 1]. En entornos reales, se usa para:
* Simular ataques dirigidos para probar la eficacia de los sistemas IDS/IPS[cite: 1].
* Automatizar la verificación de parches de seguridad en activos críticos[cite: 1].

### D. Criptografía: Clásica, Cuántica y Post-Cuántica
| Tipo | Características Principales |
| :--- | :--- |
| **Clásica** | Basada en algoritmos matemáticos complejos (RSA, AES) difíciles de resolver para computadoras actuales[cite: 1]. |
| **Cuántica** | Utiliza principios de la física cuántica (QKD) para detectar la presencia de espías en la comunicación[cite: 1]. |
| **Post-Cuántica** | Algoritmos matemáticos diseñados para ser resistentes a ataques realizados por futuras computadoras cuánticas[cite: 1]. |

### E. Blockchain y Criptomonedas
El **Blockchain** es un libro de contabilidad digital, descentralizado y distribuido que registra transacciones en múltiples computadoras[cite: 1]. En las criptomonedas, se utiliza para:
* Garantizar la inmutabilidad de las transacciones sin necesidad de un banco central[cite: 1].
* Prevenir el problema del doble gasto mediante el consenso de la red[cite: 1].

### F. Seguridad en Sistemas Biométricos
* **Protocolos:** Se utilizan estándares como **FIDO2** para autenticación segura[cite: 1].
* **Mecanismos:** Cifrado de plantillas biométricas, detección de "vida" (liveness detection) y almacenamiento en enclaves seguros (TPM)[cite: 1].

---

## 2. Parte de Diseño: Estrategia de Defensa para Bitcoin Core ⛓️

### Matriz de Amenazas (Vectores de Ataque)
| Vector de Ataque | Impacto | Probabilidad | Contramedida |
| :--- | :--- | :--- | :--- |
| **Ataque a Cadena de Suministro (GitHub)** | Muy Alto (Inyección de malware en el código) | Baja | Firma obligatoria de commits con GPG y auditoría de código por pares[cite: 1]. |
| **Ataque de Doble Gasto (Nodos)** | Alto (Pérdida de integridad financiera) | Media | Monitoreo de latencia de red y endurecimiento de la configuración de Bitcoin Core[cite: 1]. |
| **Explotación de vulnerabilidades Zero-day** | Crítico (Caída total de la red) | Media | Programa de Bug Bounty y despliegue de nodos en redes segmentadas con Firewalls[cite: 1]. |

### Informe de Metodología de Hacking Ético
1. **Reconocimiento:** Identificación de versiones de Bitcoin Core expuestas mediante escaneo de puertos (8333)[cite: 1].
2. **Escaneo:** Uso de **Nmap** y **Lynis** para encontrar configuraciones débiles en el sistema operativo del nodo[cite: 1].
3. **Explotación:** Simulación de inyección de código malicioso en el repositorio mediante credenciales robadas (Simulado en laboratorio)[cite: 1].
4. **Post-Explotación:** Instalación de un backdoor para exfiltrar las llaves privadas del nodo comprometido[cite: 1].

---

## 3. Parte Empírica: Implementación de Cadena de Bloques 💻

### Creación de un Bloque Paso a Paso
1. **Estructura:** El bloque contiene un índice, timestamp, datos (mensajes), hash anterior y su propio hash[cite: 1].
2. **Cifrado:** Se aplica el algoritmo **SHA-256** al bloque completo[cite: 1].
3. **Consenso:** El bloque es validado por los nodos antes de ser añadido a la cadena[cite: 1].

### Mensajería entre Servidores
En mi diseño, el **Servidor A** envía un mensaje cifrado que se empaqueta en el bloque actual; el **Servidor B** valida el hash del bloque anterior para confirmar la integridad del mensaje recibido[cite: 1].

### Criptografía en Blockchain
Se maneja principalmente **Criptografía Asimétrica** (Llave pública para direcciones y Llave privada para firmas) y **Funciones Hash** (como SHA-256) para enlazar los bloques de forma inmutable[cite: 1].

---
*Evaluación desarrollada para la asignatura de Seguridad de la Información - Ucompensar.*[cite: 1]
