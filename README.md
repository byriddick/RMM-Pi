# Docker Services Setup

Este repositorio contiene una configuración de múltiples servicios utilizando Docker Compose. Aquí se explica cómo funcionan cada uno de los servicios, así como las instrucciones para poner en marcha todo el sistema.

## Servicios Incluidos

1. **DuckDNS**
    - **Descripción:** Actualiza automáticamente la dirección IP pública en DuckDNS para el subdominio configurado.
    - **Detalles:** El servicio usa un token para autenticar la actualización y puede configurarse para usar direcciones IPv4.

2. **WG-Easy**
    - **Descripción:** Administra una VPN WireGuard de forma fácil con una interfaz web.
    - **Detalles:** Proporciona una interfaz para gestionar clientes y configurar el servicio VPN de forma intuitiva.

3. **Heimdall**
    - **Descripción:** Proporciona una página de inicio personalizable para acceder rápidamente a tus aplicaciones web.
    - **Detalles:** Permite agregar enlaces a las aplicaciones web que uses frecuentemente.

4. **Portainer**
    - **Descripción:** Interfaz de administración para contenedores Docker.
    - **Detalles:** Permite controlar los contenedores, redes, volúmenes y más desde un solo lugar.

5. **Node Exporter**
    - **Descripción:** Recopila métricas del sistema para monitorear el rendimiento.
    - **Detalles:** Es usado por Prometheus para recolectar métricas sobre el hardware y el sistema operativo.

6. **Prometheus**
    - **Descripción:** Plataforma de monitoreo y alerta.
    - **Detalles:** Almacena las métricas de Node Exporter y otros servicios para visualización y alertas.

7. **Grafana**
    - **Descripción:** Herramienta de visualización y análisis de datos.
    - **Detalles:** Proporciona paneles personalizables para visualizar métricas de Prometheus.

## Instrucciones de Configuración

1. **Pre-requisitos**
    - Instala [Docker](https://docs.docker.com/get-docker/) y [Docker Compose](https://docs.docker.com/compose/install/).

2. **Configuración Inicial**
    - Clona este repositorio:
      ```bash
      git clone https://github.com/tu-usuario/tu-repo.git
      ```
    - Cambia a la carpeta del proyecto:
      ```bash
      cd tu-repo
      ```
    - Crea un archivo `.env` para almacenar las variables sensibles y de entorno, como el `TOKEN` para DuckDNS y la `PASSWORD` para WG-Easy.
    - Actualiza el archivo `docker-compose.yml` con los valores necesarios, como el subdominio en DuckDNS, las rutas de volúmenes, y los puertos.

3. **Inicia los Servicios**
    - Ejecuta Docker Compose para iniciar todos los servicios:
      ```bash
      docker-compose up -d
      ```
    - Confirma que todos los contenedores están en funcionamiento:
      ```bash
      docker ps
      ```

4. **Acceso a los Servicios**
    - **DuckDNS:** No necesita acceso directo.
    - **WG-Easy:** `http://<ServerIP>:51821`
    - **Heimdall:** `https://<ServerIP>:443`
    - **Portainer:** `https://<ServerIP>:9443`
    - **Node Exporter:** `http://localhost:9100/metrics`
    - **Prometheus:** `http://<ServerIP>:9090`
    - **Grafana:** `http://<ServerIP>:3000`

5. **Volúmenes Persistentes**
   - Asegúrate de que los volúmenes definidos en el `docker-compose.yml` estén correctamente configurados para almacenar los datos de los servicios.

6. **Reinicio Automático**
   - La mayoría de los servicios están configurados para reiniciar automáticamente. Sin embargo, si deseas hacer cambios en la configuración, edita el archivo `docker-compose.yml` y reinicia con:
     ```bash
     docker-compose down && docker-compose up -d
     ```

7. **Notas Adicionales**
   - Asegúrate de cambiar las contraseñas predeterminadas y usar configuraciones seguras.
   - Consulta la documentación de cada servicio para opciones de personalización avanzadas.

---
