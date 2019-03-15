---
title: Opciones de EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: e7338c6a45d74aa8efac1b72683cca7661c62e0a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820109"
---
# <a name="editbin-options"></a>Opciones de EDITBIN

Puede utilizar EDITBIN para modificar archivos de objetos, archivos ejecutables y bibliotecas de vínculos dinámicos (DLL). Opciones especifican los cambios que realiza EDITBIN.

Una opción consta de un especificador de opción, que es un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman argumentos que se especifican precedidos de dos puntos (:). No se permiten espacios ni tabulaciones dentro de una especificación de opción. Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos. Los nombres de opción y sus argumentos de la palabra clave o argumentos de nombre de archivo no distinguen mayúsculas de minúsculas. Por ejemplo, - bind y/BIND significan lo mismo.

EDITBIN tiene las siguientes opciones:

|Opción|Propósito|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Especifica si se puede enlazar un archivo DLL.|
|[/ALLOWISOLATION](allowisolation.md)|Especifica el archivo DLL o el comportamiento de búsqueda de manifiesto del archivo ejecutable.|
|[/APPCONTAINER](appcontainer.md)|Especifica si la aplicación debe ejecutarse dentro de un AppContainer, por ejemplo, una aplicación para UWP.|
|[/BIND](bind.md)|Establece las direcciones de los puntos de entrada en los objetos especificados para acelerar el tiempo de carga.|
|[/DYNAMICBASE](dynamicbase.md)|Especifica si el archivo DLL o una imagen ejecutable puede reubicarse aleatoriamente durante la carga mediante el uso de la selección aleatoria de diseño de espacio de direcciones (ASLR).|
|[/ERRORREPORT](errorreport-editbin-exe.md)|Informes de errores internos a Microsoft.|
|[/HEAP](heap.md)|Establece el tamaño del montón de la imagen ejecutable en bytes.|
|[/HIGHENTROPYVA](highentropyva.md)|Especifica si el archivo DLL o una imagen ejecutable es compatible con alta entropía (64 bits) dirección espacio selección aleatoria del diseño (ASLR).|
|[/INTEGRITYCHECK](integritycheck.md)|Especifica si se comprueba la firma digital en tiempo de carga.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Especifica si el objeto admite las direcciones que están más de dos gigabytes.|
|[/NOLOGO](nologo-editbin.md)|Suprime la pancarta de inicio EDITBIN.|
|[/NXCOMPAT](nxcompat.md)|Especifica si la imagen ejecutable es compatible con la prevención de ejecución de datos de Windows.|
|[/REBASE](rebase.md)|Establece las direcciones base para los objetos especificados.|
|[/RELEASE](release.md)|Establece la suma de comprobación en el encabezado.|
|[/SECTION](section-editbin.md)|Invalida los atributos de una sección.|
|[/STACK](stack.md)|Establece el tamaño de pila de la imagen ejecutable en bytes.|
|[/SUBSYSTEM](subsystem.md)|Especifica el entorno de ejecución.|
|[/SWAPRUN](swaprun.md)|Especifica que la imagen ejecutable debe copiar en el archivo de intercambio y, a continuación, ejecute desde allí.|
|[/TSAWARE](tsaware.md)|Especifica que la aplicación está diseñada para ejecutarse en un entorno multiusuario.|
|[/VERSION](version.md)|Establece el número de versión en el encabezado.|

## <a name="see-also"></a>Vea también

[Herramientas de generación MSVC adicionales](c-cpp-build-tools.md)<br/>
[Referencia de EDITBIN](editbin-reference.md)
