Repositorio de Indicadores de Compromiso (IOCs)
Descripción
Este repositorio centraliza Indicadores de Compromiso (IOCs) para la detección y respuesta a incidentes de seguridad. Los datos se almacenan en formato CSV estandarizado y como reglas SIGMA para implementación directa en sistemas de detección.
Estructura del Repositorio
/
├── csv/                           # Indicadores en formato CSV
│   ├── file_hashes.csv            # Hashes de archivos maliciosos
│   ├── network_indicators.csv     # Dominios e IPs maliciosos
│   ├── system_artifacts.csv       # Artefactos en el sistema (rutas, procesos)
│   ├── persistence_mechanisms.csv # Mecanismos de persistencia
│   ├── c2_protocols.csv           # Protocolos de comando y control
│   ├── commands.csv               # Comandos utilizados por malware
│   ├── vulnerabilities.csv        # CVEs y vulnerabilidades explotadas
│   ├── targets.csv                # Sectores e industrias objetivo
│   ├── ttps.csv                   # Tácticas, técnicas y procedimientos
│   └── aliases.csv                # Nombres alternativos de amenazas
├── sigma_rules/                   # Reglas de detección en formato SIGMA
│   ├── windows/                   # Reglas específicas para Windows
│   ├── linux/                     # Reglas específicas para Linux
│   ├── network/                   # Reglas para detección en red
│   └── multi/                     # Reglas multiplataforma

Formato de los IOCs en CSV
Todos los archivos CSV utilizan el siguiente formato estandarizado:
indicator_value,indicator_type,threat_name,description,confidence,date_added,references,tags
Campos obligatorios:

indicator_value: El valor del indicador (hash, dominio, IP, etc.)
indicator_type: Tipo de indicador (md5, sha256, domain, ip, etc.)
threat_name: Nombre de la amenaza asociada
date_added: Fecha de adición en formato YYYY-MM-DD

Campos opcionales:

description: Descripción detallada del indicador
confidence: Nivel de confianza (high, medium, low)
references: Fuentes o referencias (separadas por punto y coma)
tags: Etiquetas para categorización (separadas por coma)

Reglas SIGMA
Las reglas SIGMA siguen el formato estándar YAML para detección de amenazas:

Cada regla incluye un ID único, título, descripción y nivel de severidad
Las reglas están organizadas por plataforma (Windows, Linux, etc.) y tipo de fuente de log
Se incluyen referencias a fuentes relevantes y ATT&CK TTPs cuando es posible
El nivel de falsos positivos y su potencial impacto están documentados

Cómo utilizar este repositorio
Para analistas de seguridad:

Clona el repositorio para acceso local:
git clone https://github.com/gonzalo2340/IOC.git

Importa los IOCs en formato CSV a tu SIEM o herramienta de análisis:

Los archivos CSV son compatibles con la mayoría de SIEMs y plataformas EDR
Utiliza las herramientas proporcionadas en la carpeta /tools para conversiones específicas


Implementa las reglas SIGMA en tu sistema de detección:

Utiliza herramientas como sigmac para convertir a tu formato específico
Ajusta los niveles de criticidad según tu entorno


Cómo contribuir
Las contribuciones son bienvenidas y nos ayudan a mantener una base de IOCs actualizada.

Crea un fork del repositorio
Crea una rama para tu contribución: git checkout -b nuevos-iocs
Añade tus IOCs siguiendo el formato estándar
Valida tus datos con python tools/csv_validator.py
Envía un pull request con una descripción clara de tu contribución

Requisitos para contribuciones:

Los indicadores deben incluir al menos los campos obligatorios
Proporcionar el mayor contexto posible (descripción, referencias, tags)
Evitar duplicados verificando primero los IOCs existentes
Para reglas SIGMA, asegurar que han sido probadas en un entorno de prueba

Herramientas recomendadas
Para trabajar con CSV:

csvkit: Suite de herramientas para manipulación de CSV
pandas: Biblioteca Python para análisis de datos
jq: Procesador de JSON para conversión a/desde CSV

Para reglas SIGMA:

Sigma: Herramientas y documentación oficial
Uncoder.IO: Convertidor de reglas SIGMA online
SOC Prime: Plataforma con convertidores y reglas comunitarias

Política de uso
Este repositorio está destinado exclusivamente para profesionales de seguridad informática y propósitos defensivos. El uso indebido de esta información está estrictamente prohibido.
Actualización de datos

El repositorio se actualiza regularmente con nuevos indicadores

Para preguntas, sugerencias o reportar falsos positivos:

Email: fernandez.gonzalo.gf3@gmail.com
Issues de GitHub


Nota: Mantén actualizado tu copia local del repositorio para obtener los últimos indicadores de amenazas y reglas de detección.
