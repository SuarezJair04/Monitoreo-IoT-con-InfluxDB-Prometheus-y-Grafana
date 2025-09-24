**Autor**: Suárez Castro Jair Alberto  
**Institución**: Instituto Tecnológico de Tijuana  
**Materia**: Sistemas Programables  
**Año**: 2025

# Práctica 3: Monitoreo IoT con InfluxDB, Prometheus y Grafana

## 2. Instalación y Configuración de Grafana

### 2.1 Actualización del Sistema e Instalación
Preparación del sistema mediante la actualización de la lista de paquetes y posterior instalación de Grafana desde los repositorios configurados.

![Actualización e Instalación de Grafana](images/grafana-installation-process.png)

### 2.2 Configuración del Repositorio Oficial
Se agregó la clave GPG de Grafana y se configuró el repositorio oficial utilizando el método signed-by para mayor seguridad.

![Configuración del Repositorio](images/grafana-repo-config.png)

### 2.3 Habilitación y Verificación del Servicio
Una vez instalado, se habilitó e inició el servicio de Grafana, verificando su correcto estado de ejecución en el sistema.

![Estado del Servicio Grafana](images/grafana-service-status.png)

### 2.4 Acceso a la Interfaz Web - Login Inicial
Primer acceso a la interfaz web de Grafana mediante el navegador en el puerto 3000, utilizando las credenciales por defecto.

![Página de Login de Grafana](images/grafana-login-page.png)

### 2.5 Cambio de Contraseña Obligatorio
Por seguridad, Grafana requiere el cambio de la contraseña por defecto durante el primer acceso al sistema.

![Cambio de Contraseña](images/grafana-password-change.png)

### 2.6 Panel de Bienvenida y Configuración Inicial
Interfaz principal de bienvenida que guía al usuario through los pasos iniciales de configuración, incluyendo la adición de fuentes de datos.

![Panel de Bienvenida](images/grafana-welcome-dashboard.png)
