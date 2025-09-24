**Autor**: Suárez Castro Jair Alberto  
**Institución**: Instituto Tecnológico de Tijuana  
**Materia**: Sistemas Programables  
**Año**: 2025

# Práctica 3: Monitoreo IoT con InfluxDB, Prometheus y Grafana

## 3. Instalación y Configuración de Prometheus y Node Exporter

### 3.1 Instalación de Paquetes
Instalación de Prometheus y Node Exporter mediante el gestor de paquetes apt, incluyendo todas las dependencias necesarias para el funcionamiento del sistema de monitoreo.

![Instalación de Prometheus y Node Exporter](images/prometheus-installation.png)

### 3.2 Habilitación de Servicios
Habilitación y activación de los servicios de Prometheus y Node Exporter para que se ejecuten automáticamente al inicio del sistema.

![Habilitación de Servicios](images/prometheus-enable-services.png)

### 3.3 Verificación de Puertos
Confirmación de que los servicios están escuchando en los puertos configurados (9090 para Prometheus y 9100 para Node Exporter).

![Verificación de Puertos](images/prometheus-port-verification.png)

### 3.4 Estado del Servicio Node Exporter
Verificación del estado del servicio Node Exporter, confirmando que está activo y funcionando correctamente.

![Estado de Node Exporter](images/node-exporter-status.png)

### 3.5 Estado del Servicio Prometheus
Verificación del estado del servicio Prometheus, incluyendo información detallada del proceso y recursos utilizados.

![Estado de Prometheus](images/prometheus-service-status.png)

### 3.6 Métricas del Sistema
Consulta directa a las métricas expuestas por Node Exporter, mostrando datos del sistema como garbage collection y estado de paquetes.

![Métricas del Sistema](images/system-metrics.png)

### 3.7 Interfaz Web de Prometheus - Targets
Panel de targets de Prometheus mostrando los endpoints configurados y su estado de salud (UP/DOWN).

![Targets de Prometheus](images/prometheus-targets.png)

### 3.8 Interfaz Web de Prometheus - Graph
Interfaz de consulta de Prometheus donde se pueden ejecutar queries para visualizar métricas del sistema.

![Graph de Prometheus](images/prometheus-graph-interface.png)
