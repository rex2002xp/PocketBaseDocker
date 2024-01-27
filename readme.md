# PocketBase para Docker

PocketBase es un backend de código abierto que integra una base de datos (SQLite) con suscripciones en tiempo real, gestión de autenticación incorporada, interfaz de usuario conveniente del tablero y una API REST-ish simple.

### Limite de responsabilidad.

> [!WARNING] 
> Ten en cuenta que PocketBase está en desarrollo activo y no se garantiza la retrocompatibilidad antes de llegar a la versión 1.0.0. No se recomienda para aplicaciones críticas de producción a menos que revises el [registro de cambios](https://github.com/pocketbase/pocketbase/blob/master/CHANGELOG.md) y apliques correctamente los pasos de migración manual que surgen ocasionalmente.

### Derechos de Autor y Licencia.

Este proyecto está bajo la licencia MIT. Consulta el archivo [LICENSE](LICENSE) para obtener más detalles.

Este repositorio no es una **versión oficial** para la implementación de PocketBase con Docker. Se ha creado debido a que el equipo de PocketBase no brinda soporte para Docker.

Hemos utilizado el mismo ejemplo que el equipo de PocketBase proporciona para poner en producción, llamado [Going to production](https://pocketbase.io/docs/going-to-production/).

Te animamos a conocer el repositorio oficial de [PocketBase](https://github.com/pocketbase/pocketbase) y a leer la [documentación oficial](https://pocketbase.io/docs/) que ofrecen.


### Proceso de Despliegue

El despliegue de PocketBase se puede realizar fácilmente utilizando Docker. A continuación, se proporcionan los pasos básicos para desplegar PocketBase.

1. **Clonar el Repositorio:**
   ```bash
   git clone https://tu-repositorio.git
   cd tu-repositorio
   ```
2. **Construir la Imagen Docker:**  
Asegúrate de tener Docker instalado y ejecuta el siguiente comando para construir la imagen de PocketBase.  
    ```bash
    docker buildx build --build-arg PB_VERSION="0.21.1" -t pocketbase:0.21.1 . 
    ```
3. **Ejecutar el Contenedor Docker:**   
Después de construir la imagen, ejecuta el siguiente comando para iniciar PocketBase en un contenedor Docker.   
    ```bash
    docker run -d -p 8080:8080 -v /ruta/local/pb_data:/pb/pd_data pocketbase:0.21.1
    ```   

    Ajusta `/ruta/local/pb_data` a la ruta en tu máquina local donde deseas persistir los datos. La parte después de los dos puntos (:) es la ruta dentro del contenedor donde PocketBase espera los datos (`/pb/pd_data` en tu caso).   
    
    Esta opción -v montará la carpeta local en el contenedor, lo que permite que los datos persistan incluso después de detener o eliminar el contenedor. Asegúrate de tener permisos adecuados para acceder y escribir en la carpeta local especificada.   

4. **Verificar el Despliegue:**   
Abre tu navegador y visita http://localhost:8080 para verificar que PocketBase esté funcionando correctamente.  

Recuerda personalizar los comandos según tu entorno y requisitos específicos. Además, ten en cuenta cualquier configuración adicional que pueda ser necesaria, como la conexión a bases de datos externas o la configuración de variables de entorno.


### Requisitos del Sistema

Asegúrate de cumplir con los siguientes requisitos antes de instalar y desplegar PocketBase:

1. **Docker:**
   - PocketBase se despliega en un contenedor Docker. Asegúrate de tener Docker instalado en tu sistema. Puedes descargar Docker [aquí](https://www.docker.com/get-started).

2. **Sistema Operativo:**
   - PocketBase utiliza contenedores y debería ser compatible con varios sistemas operativos. Sin embargo, se ha probado principalmente en entornos basados en Linux.

3. **Recursos de Hardware:**
   - Asegúrate de tener suficientes recursos de hardware disponibles en tu sistema para ejecutar PocketBase de manera eficiente. Esto incluye memoria RAM, capacidad de almacenamiento y poder de procesamiento.
   - Se han realizado pruebas con 1vCPU, 256MB RAM y 1GB de almacenamiento en disco /hasta 3GB pero lo mejor es mantener en constante monitoreo el servicio.


4. **Conexión a Internet:**
   - Durante el proceso de construcción de la imagen Docker, PocketBase descargará dependencias y archivos necesarios desde Internet. Asegúrate de tener una conexión a Internet estable durante este proceso.

5. **Puertos Disponibles:**
   - PocketBase expone el puerto `8080` por defecto. Asegúrate de que este puerto esté disponible y no esté siendo utilizado por otros servicios en tu sistema.

6. **Permisos:**
   - Al ejecutar el contenedor Docker, asegúrate de tener los permisos necesarios para acceder y escribir en las carpetas que PocketBase utiliza para la persistencia de datos.

Estos son los requisitos básicos para comenzar con PocketBase. Asegúrate de revisar la [documentación oficial de Docker](https://docs.docker.com/get-started/) para obtener información detallada sobre la instalación y configuración de Docker en tu sistema.



### Guía para Contribución

¡Agradecemos tu interés en contribuir a **PocketBase para Docker!** Aquí hay algunos pasos para ayudarte a comenzar:

1. **Fork del Repositorio:**
   - Haz un fork de este repositorio a tu propia cuenta utilizando el botón "Fork" en la esquina superior derecha de esta página.

2. **Clonar Repositorio Fork:**
   - Clona tu repositorio fork en tu máquina local:
     ```bash
     git clone https://github.com/TU_USUARIO/pocketbase.git
     ```

3. **Crear una Rama:**
   - Crea una nueva rama para tu contribución:
     ```bash
     cd pocketbase
     git checkout -b tu-rama
     ```

4. **Realizar Cambios:**
   - Realiza los cambios y mejoras que desees. Asegúrate de seguir las mejores prácticas de codificación y documentación.

5. **Pruebas Locales:**
   - Antes de enviar tu contribución, realiza pruebas locales para asegurarte de que todo funcione correctamente.

6. **Enviar Pull Request:**
   - Sube tus cambios a tu repositorio fork y crea un Pull Request (PR) desde tu rama a la rama principal de este repositorio.

7. **Revisión de PR:**
   - Revisaremos tu PR. Asegúrate de seguir cualquier comentario o sugerencia para facilitar el proceso de revisión.

8. **Agradecimientos:**
   - ¡Gracias por contribuir a PocketBase! Tu tiempo y esfuerzo son apreciados.

Recuerda mantener un ambiente amigable y respetuoso para todos los contribuyentes. 

¡Esperamos con interés tus contribuciones!
