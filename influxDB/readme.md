**Autor**: Suárez Castro Jair Alberto  
**Institución**: TECNM / Instituto Tecnológico de Tijuana  
**Materia**: Sistemas Programables  
**Año**: 2025

# Práctica 3: Monitoreo IoT con InfluxDB, Prometheus y Grafana

## 1. Instalación y Configuración de InfluxDB

### 1.1 Configuración del Repositorio y Clave GPG
Se agregó el repositorio oficial de InfluxData al sistema Ubuntu 20.04, configurando la clave GPG necesaria para la autenticación de paquetes.

![Configuración del Repositorio](images/influxdb-repo-config.png)

### 1.2 Proceso de Instalación
Una vez configurado el repositorio, se procedió con la instalación de InfluxDB y el cliente mediante el gestor de paquetes apt.

![Instalación de Paquetes](images/influxdb-installation-process.png)

### 1.3 Reinicio de Servicios del Sistema
Durante la instalación, el sistema identificó servicios que requerían reinicio para aplicar nuevas configuraciones y bibliotecas.

![Servicios que Requieren Reinicio](images/system-services-restart.png)

### 1.4 Sesiones de Usuario Activas
Se detectaron sesiones de usuario ejecutando binarios desactualizados, información importante para la seguridad del sistema.

![Sesiones de Usuario Activas](images/user-sessions-active.png)

### 1.5 Habilitación y Verificación del Servicio
Después de la instalación, se habilitó e inició el servicio de InfluxDB, verificando su correcto estado de ejecución.

![Estado del Servicio InfluxDB](images/influxdb-service-status.png)

### 1.6 Configuración Inicial mediante Setup Interactivo
Se ejecutó el comando `influx setup` para configurar los parámetros iniciales de la base de datos.

**Parámetros de configuración:**
- Username: jairsuarez
- Organization: SistemasProgramables  
- Bucket: sensores
- Retention Period: infinite

![Configuración Inicial](images/influxdb-setup-config.png)

### 1.7 Gestión de Tokens de API
Se listaron los tokens de autenticación disponibles, incluyendo el token de administrador generado durante la configuración inicial.

![Lista de Tokens de API](images/influxdb-tokens-list.png)

### 1.8 Interfaz Web de InfluxDB
Acceso a la interfaz gráfica de InfluxDB a través del navegador web en el puerto 8086.

![Página de Login](images/influxdb-web-login.png)

### 1.9 Panel Principal de InfluxDB
Interfaz principal de InfluxDB mostrando las opciones disponibles para escritura y consulta de datos.

![Panel Principal](images/influxdb-main-dashboard.png)

### 1.10 Verificación de Buckets Creados
Consulta mediante CLI para listar los buckets existentes, confirmando la creación del bucket "sensores".

![Lista de Buckets](images/influxdb-buckets-list.png)
