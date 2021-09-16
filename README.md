# Garantía segura

## Manual de instalacion en ambiente local 
Este documento presenta el paso a paso de instalación del proyecto garantia segura con tal de dejar una copia en su equipo con sistema operativo Windows. Este proyecto cuenta con 4 entornos los cuales son:
- UAT: En este entorno se encuentran los ultimos cambios previos a pasar a produccion, son los cambios que ve el cliente y los cambios listos para aprobación.
- PRODUCTIVO: En este entorno se encuentran los ultimos cambios los que ya han pasado por UAT y por todas las etapas de verificacion previas
- DESARROLLO: En este entorno se encuentran los cambios actuales en desarrollo, es usado por el equipo de desarrollo
- QA: Actualmente este entorno no se encuentra en uso

### Prerequisitos
Debe contar con las siguientes herramientas instaladas en su equipo:

| Herramienta                | Sitio Web                                          | Notas |
| -------------------------- | -------------------------------------------------- | ----- |
|  Sistema operativo windows |                                                    | |
| Git                        | [https://git-scm.com/download/win][PlGh]           | |
| NodeJs, Npm                | [https://nodejs.org/es/download/][PlGd]            |
| MySQL                      | [https://dev.mysql.com/downloads/installer/][PlOd] |  Al instalar esta herramienta se debe tener en cuenta la creacion a traves del mysql installer un usuario llamado: user, puesto que las migrations lo requieren
| Workbench                  | [https://dev.mysql.com/downloads/installer/][PlMe] |


### Paso a paso

1. Solicitar acceso a los siguientes repositorios, luego clonarlos en su ambiente local:
[Repositorio Frontend](https://github.com/dbsolution-computacion-e-informatica/garantia-segura-frontend.git)
[Repositorio Backend](https://github.com/dbsolution-computacion-e-informatica/garantia-segura-backend.git)
[Repositorio Infraestructura](https://github.com/dbsolution-computacion-e-informatica/garantia-segura-infrastructure.git)

2. Solicitar credenciales de la cuenta de garantia segura en AWS.

3. > Frontend
    1. Ir por medio de la consola al repositorio garantia-segura-frontend e instalar las dependencias con el siguiente comando:
    ```sh
        [garantia-segura-frontend] $ npm install
    ```
    2. Poner en marcha el fronted con el siguiente comando:
    ```sh
        [garantia-segura-frontend] $ npm run start
    ``` 
4. > Backend
    1. Ir por medio de la consola al repositorio garantia-segura-backend e instalar las dependencias con el siguiente comando:
    ```sh
        [garantia-segura-backend] $ npm install
    ```
    2. Crear la base de datos desde workbench con la siguiente query:
        ```sh
            create database garantiasegura;
        ```
    3. Generar un export de la base de datos del entorno UAT e importarlo en su entorno de base de datos local.
    4. Generar las migrations de la base de datos:
    ```sh
        [garantia-segura-backend] $ npm run migration:run
    ``` 
    5. Poner en marcha el backend con el siguiente comando:
    ```sh
        [garantia-segura-backend] $ npm run develop
    ``` 

5. Solicitar los certificados de conexion para las bases de datos y la ejecucion del backend del proyecto y posterioirmente el despliegue.

6. Conexiones a los entornos de la base de datos
    1. Acceder a su cuenta de AWS, obtener las urls y las contraseñas de conexion para las bases de datos que desea configurar
    2. En la conexion se debe seleccionar como conexion ssh y conectarse a traves de ese modo dependiendo del entorno debe seleccionar certificados productivos o no de acuerdo a lo obtenido en el paso 5.

7. Instalacion de Elastic beanstalk para despliegues
    1. Instalar Ubuntu para windows
    2. A traves de la consola de ubuntu instalada en windows se deben ejecutar los siguientes comandos:
        - Ir a la carpeta root del sistema
            ```sh
                [~]$ cd 
            ``` 
        - Instalar zip
            ```sh
                [~]$ sudo apt install zip
            ``` 
        - Instalar aws-cli
            ```sh
                [~]$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
            ``` 
        - Descomprimir el archivo descargado en el paso anterior
            ```sh
                [~]$ unzip awscliv2.zip
            ``` 
        - Ejecutar la instalación
            ```sh
                [~]$ sudo ./aws/install
            ``` 
        - Verificar instalación
            ```sh
                [~]$ aws --version
                -- aws-cli/2.1.4 Python/3.7.3 Linux/4.4.0-1
            ``` 
        - Actualizar los repositorios de ubuntu
            ```sh
                [~]$ sudo apt update
                [~]$ sudo apt upgrade
            ``` 
         - Instalar Pip3
            ```sh
                [~]$ sudo apt install python3-pip
            ``` 
         - Instalar Eb-cli
            ```sh
                [~]$ pip3 install awsebcli --upgrade --user
            ``` 
         - Configurar AWS, en este paso se deben configurar las credenciales de AWS obtenidas anterioirmente
            ```sh
                [~]$ aws configure
            ``` 