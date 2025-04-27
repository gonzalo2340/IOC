# Repositorio de Indicadores de Compromiso (IOCs)

## Descripción

Este repositorio centraliza **Indicadores de Compromiso (IOCs)** relevantes para la detección y respuesta a incidentes de seguridad. Los datos se proporcionan en dos formatos principales para facilitar su uso:

* **Formato CSV estandarizado:** Ideal para la importación en Sistemas de Gestión de Eventos e Información de Seguridad (SIEMs) y otras herramientas de análisis.
* **Reglas SIGMA:** Listas de detección en formato YAML, listas para su implementación directa en diversos sistemas de detección.

## Estructura del Repositorio

¡Claro! Vamos a darle un buen lavado de cara a ese README para que se vea más profesional y fácil de leer. Aquí tienes una versión revisada y mejorada:

Markdown

# Repositorio de Indicadores de Compromiso (IOCs)

## Descripción

Este repositorio centraliza **Indicadores de Compromiso (IOCs)** relevantes para la detección y respuesta a incidentes de seguridad. Los datos se proporcionan en dos formatos principales para facilitar su uso:

* **Formato CSV estandarizado:** Ideal para la importación en Sistemas de Gestión de Eventos e Información de Seguridad (SIEMs) y otras herramientas de análisis.
* **Reglas SIGMA:** Listas de detección en formato YAML, listas para su implementación directa en diversos sistemas de detección.

## Estructura del Repositorio

/
├── csv/
│   ├── file_hashes.csv          # Hashes de archivos maliciosos (MD5, SHA1, SHA256, etc.)
│   ├── network_indicators.csv   # Dominios, direcciones IP y URLs maliciosas
│   ├── system_artifacts.csv     # Artefactos relevantes en sistemas (rutas de archivos, nombres de procesos, claves de registro, etc.)
│   ├── persistence_mechanisms.csv # Técnicas de persistencia utilizadas por malware
│   ├── c2_protocols.csv         # Patrones de comunicación de Comando y Control (C2)
│   ├── commands.csv             # Comandos comúnmente utilizados por software malicioso
│   ├── vulnerabilities.csv      # Identificadores CVE de vulnerabilidades explotadas
│   ├── targets.csv              # Sectores e industrias que son blanco de ataques
│   ├── ttps.csv                 # Tácticas, Técnicas y Procedimientos (TTPs) observados
│   └── aliases.csv              # Nombres alternativos o alias de grupos o amenazas
├── sigma_rules/
│   ├── windows/               # Reglas SIGMA específicas para sistemas Windows
│   ├── linux/                 # Reglas SIGMA específicas para sistemas Linux
│   ├── network/               # Reglas SIGMA para la detección en el tráfico de red
│   └── multi/                 # Reglas SIGMA multiplataforma o aplicables a varios entornos

## Formato de los IOCs en CSV

Todos los archivos CSV dentro del directorio `/csv/` siguen el siguiente formato estandarizado para garantizar la consistencia y facilitar la importación:

| Campo             | Requerido | Descripción                                                                 | Ejemplo(s)                                      |
| ----------------- | :-------: | --------------------------------------------------------------------------- | ------------------------------------------------ |
| `indicator_value` |    Sí     | El valor del indicador específico.                                          | `275a021bbfb6489e54d471899f7db9d1663fc695ec2fe2a2c4538aabf7017293`, `malicious.domain.com`, `192.168.1.100` |
| `indicator_type`  |    Sí     | El tipo de indicador.                                                      | `sha256`, `domain`, `ip`, `url`, `registry_key` |
| `threat_name`     |    Sí     | El nombre de la amenaza o grupo asociado al indicador (si se conoce).      | `Emotet`, `APT32`, `Cobalt Strike`              |
| `date_added`      |    Sí     | Fecha en la que se añadió el indicador al repositorio (formato `AAAA-MM-DD`). | `2023-10-26`                                     |
| `description`     |    No     | Detalles adicionales o contexto sobre el indicador.                         | `Servidor C2 utilizado en la campaña de Octubre de 2023.`, `Archivo dropper inicial.` |
| `confidence`      |    No     | Nivel de confianza en la validez del indicador (`high`, `medium`, `low`).   | `high`                                           |
| `references`      |    No     | Fuentes o referencias relevantes (separadas por punto y coma `;`).           | `MITRE ATT&CK T1071; CISA AA23-281A`             |
| `tags`            |    No     | Etiquetas para facilitar la categorización y búsqueda (separadas por coma `,`). | `phishing`, `ransomware`, `reconnaissance`       |

## Reglas SIGMA

Las reglas de detección SIGMA, ubicadas en el directorio `/sigma_rules/`, están escritas en formato YAML estándar y diseñadas para ser convertidas a diferentes formatos de SIEM y EDR. Cada regla sigue una estructura común que incluye:

* **`id`:** Un identificador único para la regla.
* **`title`:** Un título descriptivo de la regla.
* **`description`:** Una explicación detallada de lo que la regla detecta.
* **`level`:** El nivel de severidad de la alerta (`informational`, `low`, `medium`, `high`, `critical`).
* **`logsource`:** Define la fuente de los logs a analizar (ej: `category: process_creation`, `product: windows`).
* **`detection`:** La lógica principal de detección, utilizando un lenguaje de consulta específico de SIGMA.
* **`references`:** Enlaces a documentación relevante, análisis de amenazas o artículos.
* **`tags`:** Etiquetas para categorizar la regla, incluyendo posibles mapeos a MITRE ATT&CK (`attack.t1566`).
* **`falsepositives`:** Posibles escenarios que podrían generar falsos positivos.
* **`impact`:** El potencial impacto de la actividad detectada.

Las reglas están organizadas por plataforma y tipo de fuente de log para facilitar su localización y aplicación.

## Cómo utilizar este repositorio

### Para analistas de seguridad:

1.  **Clonar el repositorio:**
    ```bash
    git clone [https://github.com/gonzalo2340/IOC.git](https://github.com/gonzalo2340/IOC.git)
    ```

2.  **Importar los IOCs en formato CSV:**
    * Los archivos CSV son compatibles con la mayoría de las plataformas SIEM y EDR.
    * Utilice las herramientas proporcionadas en la carpeta `/tools/` (si existen) para conversiones o validaciones específicas.

3.  **Implementar las reglas SIGMA:**
    * Utilice herramientas como [sigmac](https://github.com/SigmaHQ/sigma) para convertir las reglas SIGMA al formato específico de su sistema de detección.
    * Ajuste los niveles de criticidad y las reglas según las necesidades y el contexto de su entorno.

## Cómo contribuir

¡Tu contribución es valiosa para mantener este repositorio actualizado y útil para la comunidad de seguridad! Para contribuir:

1.  **Crea un fork del repositorio** en tu cuenta de GitHub.
2.  **Crea una rama** para tus contribuciones:
    ```bash
    git checkout -b feature/nuevos-iocs
    ```
3.  **Añade tus IOCs** al archivo CSV correspondiente siguiendo el formato estándar.
4.  **Valida tus datos** utilizando las herramientas de validación proporcionadas (si existen en `/tools/`). Por ejemplo (si existe un script de validación en Python):
    ```bash
    python tools/csv_validator.py csv/tu_archivo.csv
    ```
5.  **Envía un pull request** a la rama `main` del repositorio con una descripción clara y concisa de tus contribuciones.

### Requisitos para contribuciones:

* Los indicadores deben incluir **al menos los campos obligatorios** definidos en la sección "Formato de los IOCs en CSV".
* Proporciona el **mayor contexto posible** para cada indicador (descripción, referencias, etiquetas relevantes).
* **Evita duplicados** verificando cuidadosamente los IOCs existentes antes de añadir nuevos.
* Para las **reglas SIGMA**, asegúrate de que han sido **probadas en un entorno de prueba** y que incluyen información clara sobre su propósito, posibles falsos positivos y referencias.

## Herramientas recomendadas

Aquí tienes algunas herramientas que pueden ser útiles para trabajar con los datos de este repositorio:

### Para trabajar con CSV:

* **[csvkit](https://csvkit.readthedocs.io/en/latest/):** Un conjunto de utilidades de línea de comandos para trabajar con archivos CSV.
* **[pandas](https://pandas.pydata.org/):** Una poderosa biblioteca de Python para el análisis y manipulación de datos.
* **[jq](https://stedolan.github.io/jq/):** Un procesador de JSON ligero y flexible que también puede utilizarse para convertir entre JSON y CSV.

### Para reglas SIGMA:

* **[SigmaHQ](https://github.com/SigmaHQ/sigma):** El repositorio oficial de SIGMA, con documentación, herramientas y reglas comunitarias.
* **[Uncoder.IO](https://uncoder.io/):** Una plataforma online para convertir reglas SIGMA a diferentes formatos y viceversa.
* **[SOC Prime](https://socprime.com/):** Una plataforma con una amplia colección de reglas SIGMA y herramientas de conversión.

## Política de uso

Este repositorio se proporciona **exclusivamente para profesionales de seguridad informática y con fines defensivos**. Se prohíbe estrictamente el uso indebido de la información contenida en este repositorio para actividades maliciosas o cualquier otro propósito ilegal.

## Actualización de datos

Este repositorio se actualiza de forma regular con nuevos indicadores de amenazas y reglas de detección para mantenerlo relevante y útil. **Se recomienda mantener actualizada tu copia local del repositorio** para beneficiarte de las últimas incorporaciones.

## Contacto

Para preguntas, sugerencias o para reportar posibles falsos positivos, por favor utiliza los siguientes canales:

* **Email:** [fernandez.gonzalo.gf3@gmail.com](mailto:fernandez.gonzalo.gf3@gmail.com)
* **GitHub Issues:** Abre un nuevo "Issue" en este repositorio para reportar problemas o sugerencias.

---

**Nota:** ¡Mantén tu copia local del repositorio actualizada para obtener los últimos indicadores de amenazas y reglas de detección!

