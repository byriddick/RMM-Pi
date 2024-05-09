# RMM-Pi

**RMM-Pi** es un conjunto de herramientas de monitoreo remoto y administración construido para dispositivos como Raspberry Pi. Este proyecto incluye varios servicios configurados con Docker Compose que ofrecen administración de VPN, monitoreo de métricas y más.

## Servicios Incluidos

1. **DuckDNS**
    - **Descripción:** Actualiza automáticamente la dirección IP pública para un subdominio en DuckDNS.
    - **Configuración:** Se usa un token para la autenticación, y está configurado para actualizar usando direcciones IPv4.

2. **WG-Easy**
    - **Descripción:** Simplifica la configuración y administración de una VPN WireGuard.
    - **Detalles:** Proporciona una interfaz gráfica para agregar y eliminar clientes.

3. **Heimdall**
    - **Descripción:** Una página de inicio personalizable para tus aplicaciones web.
    - **Detalles:** Centraliza enlaces a las aplicaciones y servicios de tu red.

4. **Portainer**
    - **Descripción:** Interfaz de administración para contenedores Docker.
    - **Detalles:** Permite controlar todos los servicios Docker en tu sistema desde una sola ubicación.

5. **Node Exporter**
    - **Descripción:** Recopila métricas de hardware y del sistema para Prometheus.
    - **Detalles:** Proporciona datos sobre el uso de CPU, memoria y más.

6. **Prometheus**
    - **Descripción:** Plataforma de monitoreo y alerta.
    - **Detalles:** Almacena métricas de Node Exporter para visualización y alertas.

7. **Grafana**
    - **Descripción:** Herramienta de visualización de datos para analizar métricas.
    - **Detalles:** Ofrece paneles personalizados para las métricas recopiladas por Prometheus.

## Requisitos

- Raspberry Pi (preferiblemente con una distribución basada en Linux).
- [Docker](https://docs.docker.com/get-docker/) y [Docker Compose](https://docs.docker.com/compose/install/).

## Configuración Inicial

1. Clona este repositorio:
    ```bash
    git clone https://github.com/byriddick/RMM-Pi.git
    ```
2. Accede a la carpeta del proyecto:
    ```bash
    cd RMM-Pi
    ```
3. Configura las variables de entorno en un archivo `.env`:
    - **DuckDNS:** Agrega el token de autenticación y los subdominios.
    - **WG-Easy:** Configura el host y la contraseña para la administración.
    - **Portainer:** Cambia las contraseñas predeterminadas.

4. Modifica el archivo `docker-compose.yml` si es necesario, para ajustar los puertos, rutas de volúmenes u otras configuraciones.

## Iniciando los Servicios

1. Inicia todos los servicios con:
    ```bash
    docker-compose up -d
    ```
2. Verifica que todos los contenedores están activos:
    ```bash
    docker ps
    ```

## Acceso a los Servicios

- **DuckDNS:** No requiere acceso directo.
- **WG-Easy:** `http://<WG_HOST>:51821`
- **Heimdall:** `http://localhost`
- **Portainer:** `https://localhost:9443`
- **Node Exporter:** `http://localhost:9100/metrics`
- **Prometheus:** `http://localhost:9090`
- **Grafana:** `http://localhost:3000`

## Volúmenes Persistentes

Asegúrate de que los volúmenes definidos en `docker-compose.yml` estén configurados para mantener la persistencia de datos.

## Reinicio Automático

Para realizar cambios en la configuración:

1. Modifica el archivo `docker-compose.yml`.
2. Reinicia los servicios:
    ```bash
    docker-compose down && docker-compose up -d
    ```

## Notas Adicionales

- Cambia las contraseñas predeterminadas para seguridad.
- Consulta la documentación de cada servicio para personalizar más configuraciones.

---

Espero que este `README.md` sea útil. Puedes ajustar el contenido según las necesidades específicas de tu proyecto.
