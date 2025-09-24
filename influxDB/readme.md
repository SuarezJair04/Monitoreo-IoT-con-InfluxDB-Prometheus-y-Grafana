**Autor**: Suárez Castro Jair Alberto  
**Institución**: TECNM / Instituto Tecnológico de Tijuana  
**Materia**: Sistemas Programables  
**Año**: 2025

# Práctica 3: Monitoreo IoT con InfluxDB, Prometheus y Grafana

## 1. Instalación y Configuración de InfluxDB

### 1.1 Configuración del Repositorio y Clave GPG
Se agregó el repositorio oficial de InfluxData al sistema Ubuntu 20.04, configurando la clave GPG necesaria para la autenticación de paquetes.

<img width="904" height="106" alt="Image" src="https://github.com/user-attachments/assets/fba6fde7-d1b6-4151-bf61-e82eb491c8ea" />

### 1.2 Proceso de Instalación
Una vez configurado el repositorio, se procedió con la instalación de InfluxDB y el cliente mediante el gestor de paquetes apt.

```debug
sudo apt update
sudo apt install -y influxdb2
```

### 1.3 Reinicio de Servicios del Sistema
Durante la instalación, el sistema identificó servicios que requerían reinicio para aplicar nuevas configuraciones y bibliotecas.



### 1.4 Habilitación y Verificación del Servicio
Después de la instalación, se habilitó e inició el servicio de InfluxDB, verificando su correcto estado de ejecución.

<img width="906" height="321" alt="Image" src="https://github.com/user-attachments/assets/5582d2d2-d03f-4d06-80c4-915d39629b50" />

### 1.5 Configuración Inicial mediante Setup Interactivo
Se ejecutó el comando `influx setup` para configurar los parámetros iniciales de la base de datos.

**Parámetros de configuración:**
- Username: jairsuarez
- Organization: SistemasProgramables  
- Bucket: sensores
- Retention Period: infinite
  
<img width="907" height="392" alt="Image" src="https://github.com/user-attachments/assets/3cd70044-2761-4caa-be3e-d592e362ca5d" />

### 1.6 Gestión de Tokens de API
Se listaron los tokens de autenticación disponibles, incluyendo el token de administrador generado durante la configuración inicial.

<img width="1017" height="124" alt="Image" src="https://github.com/user-attachments/assets/df864780-7dd7-4e75-88c6-e3f7c9c3de10" />

### 1.7 Interfaz Web de InfluxDB
Acceso a la interfaz gráfica de InfluxDB a través del navegador web en el puerto 8086.

<img width="906" height="439" alt="Image" src="https://github.com/user-attachments/assets/afabf12f-0fd8-4e55-b446-04b7a2726ee7" />


### 1.8 Panel Principal de InfluxDB
Interfaz principal de InfluxDB mostrando las opciones disponibles para escritura y consulta de datos.

<img width="901" height="428" alt="Image" src="https://github.com/user-attachments/assets/344b6b9a-c631-4cfb-ab5f-e9b1b9163657" />

### 1.9 Verificación de Buckets Creados
Consulta mediante CLI para listar los buckets existentes, confirmando la creación del bucket "sensores".

<img width="908" height="102" alt="Image" src="https://github.com/user-attachments/assets/7f32933d-b52e-4844-be5d-65a45dc8b9f5" />
