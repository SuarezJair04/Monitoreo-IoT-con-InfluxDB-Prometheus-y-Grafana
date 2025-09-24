# Práctica 3: Monitoreo IoT con InfluxDB, Prometheus y Grafana

**Autor:** Suárez Castro Jair Alberto  
**Institución:** Instituto Tecnológico de Tijuana  
**Materia:** Sistemas Programables  
**Año:** 2025

## Descripción del Proyecto

Este repositorio documenta la implementación de una solución completa de monitoreo para aplicaciones de Internet de las Cosas (IoT). El proyecto integra tres tecnologías fundamentales para la observabilidad de sistemas:

- **InfluxDB** para el almacenamiento de series temporales de datos de sensores
- **Prometheus** para la recolección de métricas de infraestructura
- **Grafana** para la visualización unificada de datos

La infraestructura se despliega en una instancia Amazon EC2, utilizando Tailscale VPN para garantizar la seguridad de las conexiones.

## Arquitectura de la Solución

El diseño implementado consiste en un servidor central en EC2 que alberga toda la plataforma de monitoreo. Los datos simulados de sensores IoT se envían a InfluxDB, mientras que Prometheus recolecta métricas del estado del servidor mediante Node Exporter. Grafana se conecta a ambas fuentes de datos para proporcionar una visualización centralizada en un dashboard único.

## Componentes del Sistema

| Componente | Versión | Propósito | Puerto |
|------------|---------|-----------|---------|
| InfluxDB | 2.7.x | Almacenamiento datos IoT | 8086 |
| Prometheus | 3.5.x | Métricas del sistema | 9090 |
| Node Exporter | 1.9.x | Exportar métricas del servidor | 9100 |
| Grafana | 10.x | Dashboard y visualización | 3000 |
| Tailscale | 1.5.x | VPN segura | - |

## Desarrollo de la Práctica

### 1. Configuración de Tailscale (20%)

Se implementó una VPN utilizando Tailscale para interconectar de manera segura la instancia EC2 con los dispositivos personales. Esta aproximación eliminó la necesidad de abrir puertos públicos, incrementando significativamente la seguridad del sistema.

**Evidencia:** Captura del panel de administración de Tailscale mostrando los dispositivos conectados.

![Image](https://github.com/user-attachments/assets/3553e49a-6bee-44bd-bf4c-e351c1198303)

### 2. Instalación de InfluxDB (15%)

- Instalación desde el repositorio oficial siguiendo las mejores prácticas actuales
- Configuración de organización, bucket y token de autenticación
- Verificación del correcto funcionamiento del servicio
  
[Instalación de InfluxDB](./influxDB/readme.md)

### 3. Instalación de Prometheus y Node Exporter (15%)

- Configuración de servicios mediante systemd para garantizar su ejecución continua
- Actualización del archivo de configuración prometheus.yml para el monitoreo de endpoints
- Validación de la recolección de métricas del sistema

[Instalación de Prometheus](./prometheus/readme.md)

### 4. Instalación de Grafana (15%)

- Instalación y habilitación del servicio de Grafana
- Configuración de fuentes de datos para conectar con InfluxDB y Prometheus
- Verificación de la conectividad con ambas plataformas

[Instalación de Grafana](./grafana/readme.md)

### 5. Simulación de Datos IoT (15%)

Se desarrolló un script en Python que simula el comportamiento de sensores de temperatura y humedad, enviando lecturas periódicas a InfluxDB cada 5 segundos.

```python
from datetime import datetime
import random
import time
from influxdb_client import InfluxDBClient, Point, WritePrecision

# Configuración de conexión a InfluxDB
token = "token_de_acceso"
org = "SistemasProgramables"
bucket = "sensores"

# Establecimiento de conexión con el servidor InfluxDB
client = InfluxDBClient(url="http://localhost:8086", token=token, org=org)
write_api = client.write_api()

# Bucle principal de generación de datos
while True:
    temperatura = random.uniform(18, 30)
    humedad = random.uniform(40, 70)
    punto_datos = (
        Point("ambiente")
        .tag("ubicacion", "laboratorio")
        .field("temperatura", temperatura)
        .field("humedad", humedad)
        .time(datetime.utcnow(), WritePrecision.NS)
    )
    write_api.write(bucket=bucket, record=punto_datos)
    print(f"Datos enviados: temperatura={temperatura:.2f}, humedad={humedad:.2f}")
    time.sleep(5)
```
### 6. Dashboard en Grafana (15%)

Se creó un dashboard unificado que integra métricas IoT desde InfluxDB con métricas de sistema desde Prometheus y Node Exporter, proporcionando una visión completa del estado del sistema.

**Características del Dashboard:**
- **Panel de Temperatura**: Gráfico de series temporales con datos de InfluxDB
- **Panel de Humedad**: Monitoreo de humedad ambiental en tiempo real
- **Métricas de Sistema**: Uso de CPU, memoria RAM y recursos del servidor
- **Actualización automática**: Refresh cada 5 segundos para datos en tiempo real

**Tecnologías integradas:**
- **Flux Query Language** para consultas a InfluxDB
- **PromQL** para consultas a Prometheus
- **Visualizaciones unificadas** en una sola interfaz

![Image](https://github.com/user-attachments/assets/bdaf2a60-045e-42e1-a9bf-73a12e5c1f59)
![Image](https://github.com/user-attachments/assets/6593ae0d-6f33-4202-b622-7234bd868427)

## Video Demostración

[!Ver Video Demo](https://www.youtube.com/watch?v=DWGQMuYsQzY)

### 📋 Contenido del video:
- Dashboard de Grafana en tiempo real
- Datos de temperatura/humedad desde InfluxDB
- Métricas del sistema con Prometheus
- Configuración de paneles y visualizaciones
- Navegación por la interfaz completa

[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-flat&logo=youtube&logoColor=white)]([https://youtu.be/TU_VIDEO_ID_AQUI](https://youtu.be/DWGQMuYsQzY))

### 7. Informe Escrito y Reflexiones (5%)

#### Ventajas de Tailscale en este escenario

Tailscale permite establecer una VPN en malla entre los dispositivos y el servidor EC2, evitando la exposición de puertos públicos como el 3000 para Grafana o el 9090 para Prometheus. Esta aproximación reduce significativamente la superficie de ataque y garantiza que solo los dispositivos autorizados dentro de la red Tailscale puedan acceder a los servicios.

#### Diferencias entre métricas IoT y de infraestructura

| Aspecto | Métricas IoT (InfluxDB) | Métricas de Infraestructura (Prometheus) |
|---------|-------------------------|------------------------------------------|
| **Origen de datos** | Sensores y dispositivos IoT | Servidores y recursos de sistema |
| **Ejemplos típicos** | Temperatura, humedad, presión | Uso de CPU, memoria, disco, red |
| **Propósito principal** | Monitorear procesos y ambiente físico | Monitorear salud de infraestructura TI |
| **Frecuencia de muestreo** | Alta (segundos) | Media (minutos) |
| **Tipo de datos** | Datos de aplicación/sensores | Métricas de sistema operativo |
| **Almacenamiento** | Series temporales optimizadas | Métricas dimensionales |


