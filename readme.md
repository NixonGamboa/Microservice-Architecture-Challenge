# Sistema de Gestion de Cuentas y Usuarios
![java-toolkit](https://img.shields.io/badge/Java17-Toolkit-important?logo=java)
![java-toolkit](https://img.shields.io/badge/Oracle-SQL-blue)
![java-toolkit](https://img.shields.io/badge/Gradle-Build-yellow)

## 1. Pre-Requisitos
* Tener instalado [**Java 17**](https://www.oracle.com/java/technologies/downloads/).
* Tener instalado [**Gradle 8.1.1**](https://gradle.org/install/).
* Tener instalado [**Podman v4.7+**](https://podman.io/docs/installation). Si usas Windows y tienes problemas con la
  ejecución de Podman, puedes ver esta [guía](https://blog.scottlogic.com/2022/02/15/replacing-docker-desktop-with-podman.html).



## 2. Configurar el entorno

* Descargar los repositorios de los microservicios:
    ```shell script
    git clone https://github.com/NixonGamboa/ms-users-challenge.git
    ```
    ```shell script
    git clone https://github.com/NixonGamboa/ms-accounting-transactions-challenge.git
    ``` 
> **Nota:** Configurar los archivos aplication.yaml de cada uno de los modulos segun se requiera.

 #### Puede acceder directamente a los repositorios de *GitHub* desde aqui:
-  [***ms-users-challenge***](https://github.com/NixonGamboa/ms-users-challenge.git)
-  [***ms-accounting-transactions-challenge***](https://github.com/NixonGamboa/ms-accounting-transactions-challenge.git)

## 3. Compilar y desplegar el Sistema

* Compilar el ms-users: 
    ```shell script
    cd ms-users-challenge; ./gradlew bootJar; cd ..
    ``` 
  Esto genera el archivo `ms-users.jar` en el directorio `/ms-users-challenge/runner/app-service/build/libs`

  
* Compilar el ms-accounting-transactions:
    ```shell script
    cd ms-accounting-transactions-challenge; ./gradlew bootJar; cd ..
    ``` 
   Esto genera el archivo `accounting-transactions.jar` en el directorio
   `/ms-accounting-transactions-challenge/runner/app-service/build/libs`


* Ejecutar el compose donde está configurado el ambiente de los 2 microservicios más la creacion de la base de datos:
    ```shell script
    podman compose up
    ``` 

## 4. Probar la aplicacion

> **Nota:** Si la configuracion de la base de datos en `application-oracle-env.yaml` establece la propiedad
> `hibernate.ddl-auto: none` o cualquiera de similar comportamiento, es probable que requiera ejecutar manuealmente en su base de datos el siguiente script:
>
> * [***script01_create_tables.sql***](script01_create_tables.sql)


> **Nota:** Puede importar en Postman las colecciones de ejemplo para cada microservicio desde los archivos:
> * [***ms-users-challenge.postman_collection***](ms-users-challenge.postman_collection.json)
> * [***ms-accounting-transactions-challenge.postman_collection***](ms-accounting-transactions-challenge.postman_collection.json)
