# Transbank Woocommerce Webpay

Plugin oficial de Woocommerce para Webpay

## Descripción

Este plugin **oficial** ha sido creado para que puedas integrar Webpay fácilmente en tu comercio, basado en Woocommerce.
Está basado en el SDK oficial de PHP [SDK PHP de Webpay](https://github.com/TransbankDevelopers/transbank-sdk-php).

### ¿Cómo instalar?
Puedes ver instrucciones de instalación y documentación en [https://www.transbankdevelopers.cl/plugin/woocommerce/](https://www.transbankdevelopers.cl/plugin/woocommerce/)

### Paso a producción
Al instalar el plugin, este vendrá configurado para funcionar en modo '**integración**'(en el ambiente de pruebas de Transbank). Para poder operar con dinero real (ambiente de **producción**), debes:
1.- Tener tu propio código de comercio. Si no lo tienes, solicita Webpay Plus en [transbank.cl](https://transbank.cl)
2.- Debes [generar tus credenciales](https://www.transbankdevelopers.cl/documentacion/como_empezar#credenciales-en-webpay) (llave privada y llave pública)
3.- Enviar la planilla de validación a soporte@transbank.cl, junto con la llave pública (generada en el paso anterior) y tu logo. 
4.- Cuando Transbank confirme que ha cargado tu certificado público y logo, debes entrar a la pantalla de configuración del plugin dentro de WooCommerce y colocar tu código de comercio, llave privada, llave pública y poner el ambiente de 'Producción'. 

Puedes ver más información acá: [https://www.transbankdevelopers.cl/documentacion/como_empezar#credenciales-en-webpay](https://www.transbankdevelopers.cl/documentacion/como_empezar#credenciales-en-webpay)


## Requisitos 
* PHP 5.6 o superior
* Woocommerce 3.4 o superior

## Dependencias

El plugin depende de las siguientes librerías:

* transbank/transbank-sdk
* tecnickcom/tcpdf
* apache/log4php

Para cumplir estas dependencias, debes instalar [Composer](https://getcomposer.org), e instalarlas con el comando `composer install`.

## Nota  
- La versión del sdk de php se encuentra en el archivo `woocommerce-transbank/composer.json`

## Desarrollo

Para apoyar el levantamiento rápido de un ambiente de desarrollo, hemos creado la especificación de contenedores a través de Docker Compose.

Para usarlo seguir el siguiente [README Woocommerce 3.4.0 con php 7.2](./docker-woocommerce-php7.2)  

### Actualizar versión del SDK de Transbank
Para actualizar la versión del SDK de Transbank se debe editar el archivo `woocommerce-transbank/composer.json` y cambiar
el valor de la propiedad `"transbank/transbank-sdk"` por la versión que se desea instalar y luego ejecutar el bash `update`
que esta en la carpeta `docker-woocommerce-php7.2` lo que actualizara la dependencia del plugin.

### Crear el instalador del plugin

    ./package.sh

## Generar una nueva versión

Para generar una nueva versión, se debe crear un PR (con un título "Prepare release X.Y.Z" con los valores que correspondan para `X`, `Y` y `Z`). Se debe seguir el estándar semver para determinar si se incrementa el valor de `X` (si hay cambios no retrocompatibles), `Y` (para mejoras retrocompatibles) o `Z` (si sólo hubo correcciones a bugs).

En ese PR deben incluirse los siguientes cambios:

1. Modificar el archivo CHANGELOG.md para incluir una nueva entrada (al comienzo) para `X.Y.Z` que explique en español los cambios.

Luego de obtener aprobación del pull request, debes mezclar a master e inmediatamente generar un release en GitHub con el tag `vX.Y.Z`. En la descripción del release debes poner lo mismo que agregaste al changelog.

Con eso Travis CI generará automáticamente una nueva versión del plugin y actualizará el Release de Github con el zip del plugin.
