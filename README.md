# Garantía segura

## Manual de instalacion en ambiente local 
Este documento presenta el paso a paso de instalación del proyecto garantia segura con tal de dejar una copia en su equipo con sistema operativo Windows. 

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
