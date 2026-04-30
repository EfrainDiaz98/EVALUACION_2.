# Evaluación 2 - Seguridad de la Información 🛡️
**Estudiante:** Efrain Yair Diaz Anzola  
**Institución:** Fundación Universitaria Compensar  
**Facultad:** Ingeniería de Telecomunicaciones[cite: 1]

---

## 1. Parte Conceptual 📚

### A. Reconocimiento en Footprinting
* **Reconocimiento Pasivo:** Se realiza sin interactuar directamente con el objetivo, utilizando fuentes públicas como Shodan o WHOIS[cite: 1].
* **Reconocimiento Activo:** Implica interacción directa con el sistema, como el escaneo de puertos mediante Nmap[cite: 1].

### B. Exploits, Payloads y Post-Exploits
* **Exploit:** Código o técnica que aprovecha una vulnerabilidad específica[cite: 1].
* **Payload:** Código que se ejecuta en el sistema víctima tras una explotación exitosa[cite: 1].
* **Post-Exploit:** Acciones para mantener el control del sistema o escalar privilegios[cite: 1].

**Ejemplos:**
1. **Exploit:** EternalBlue (MS17-010)[cite: 1].
2. **Payload:** Meterpreter de Metasploit[cite: 1].

### C. Metasploit en Entornos Reales
Metasploit permite validar vulnerabilidades y probar la efectividad de las defensas de red (IDS/IPS) simulando ataques reales en un entorno controlado[cite: 1].

### D. Criptografía: Clásica, Cuántica y Post-Cuántica
| Tipo | Características Principales |
| :--- | :--- |
| **Clásica** | Basada en algoritmos como RSA o AES[cite: 1]. |
| **Cuántica** | Utiliza la física de partículas para comunicaciones ultra seguras[cite: 1]. |
| **Post-Cuántica** | Algoritmos matemáticos resistentes a la futura computación cuántica[cite: 1]. |

### E. Blockchain y Criptomonedas
Blockchain es un registro descentralizado e inmutable[cite: 1]. Se usa en criptomonedas para evitar el fraude y eliminar intermediarios financieros[cite: 1].

### F. Seguridad en Sistemas Biométricos
Se utilizan protocolos como FIDO2 y mecanismos de cifrado para proteger las plantillas biométricas almacenadas[cite: 1].

---

## 2. Parte de Diseño: Estrategia para Bitcoin Core ⛓️

### Matriz de Amenazas
| Vector de Ataque | Impacto | Probabilidad | Contramedida |
| :--- | :--- | :--- | :--- |
| **Cadena de Suministro** | Muy Alto | Baja | Firma GPG en commits de GitHub[cite: 1]. |
| **Ataque de Nodos** | Alto | Media | Segmentación de red y Firewalls[cite: 1]. |

### Fases del Hacking Ético Aplicado
1. **Reconocimiento:** Identificación de nodos Bitcoin activos[cite: 1].
2. **Escaneo:** Análisis de vulnerabilidades en el servicio Bitcoin Core[cite: 1].
3. **Explotación:** Intento de compromiso del nodo mediante exploits conocidos[cite: 1].
4. **Post-Explotación:** Evaluación de la persistencia y acceso a llaves privadas[cite: 1].

---

## 3. Parte Empírica: Implementación de Blockchain 💻

### Creación de Bloques y Funcionalidad
La cadena de bloques funciona mediante la vinculación de bloques a través de hashes únicos[cite: 1]. El proceso incluye:
1. **Bloque Génesis:** El primer bloque de la cadena con hash previo en '0'[cite: 1].
2. **Hash de Seguridad:** Generado mediante el algoritmo SHA-256[cite: 1].

### Código de Implementación (Python)
A continuación, se detalla la lógica de creación y hashing de la cadena:
```python
import hashlib
import json
from time import time

class Blockchain:
    def __init__(self):
        self.chain = [] # Crear el primer bloque (Bloque Génesis)
        self.create_block(proof=1, previous_hash='0', data="Bloque Génesis")

    def create_block(self, proof, previous_hash, data):
        block = {
            'index': len(self.chain) + 1,
            'timestamp': time(),
            'data': data,
            'proof': proof,
            'previous_hash': previous_hash
        }
        # Se genera el sello de seguridad usando SHA-256
        block['hash'] = self.hash(block)
        self.chain.append(block)
        return block

    def hash(self, block):
        # El bloque se convierte en texto para poder generar el hash
        encoded_block = json.dumps(block, sort_keys=True).encode()
        return hashlib.sha256(encoded_block).hexdigest()
