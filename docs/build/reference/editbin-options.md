---
title: Opciones de EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: 263cfb79897ae60daff64521928db865f1dcb874
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540548"
---
# <a name="editbin-options"></a>Opciones de EDITBIN

Puede utilizar EDITBIN para modificar archivos de objetos, archivos ejecutables y bibliotecas de vínculos dinámicos (DLL). Opciones especifican los cambios que realiza EDITBIN.

Una opción consta de un especificador de opción, que es un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman argumentos que se especifican precedidos de dos puntos (:). No se permiten espacios ni tabulaciones dentro de una especificación de opción. Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos. Los nombres de opción y sus argumentos de la palabra clave o argumentos de nombre de archivo no distinguen mayúsculas de minúsculas. Por ejemplo, - bind y/BIND significan lo mismo.

EDITBIN tiene las siguientes opciones:

|Opción|Propósito|
|------------|-------------|
|[/ALLOWBIND](../../build/reference/allowbind.md)|Especifica si se puede enlazar un archivo DLL.|
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|Especifica el archivo DLL o el comportamiento de búsqueda de manifiesto del archivo ejecutable.|
|[/APPCONTAINER](../../build/reference/appcontainer.md)|Especifica si la aplicación debe ejecutarse dentro de un AppContainer, por ejemplo, una aplicación para UWP.|
|[/BIND](../../build/reference/bind.md)|Establece las direcciones de los puntos de entrada en los objetos especificados para acelerar el tiempo de carga.|
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|Especifica si el archivo DLL o una imagen ejecutable puede reubicarse aleatoriamente durante la carga mediante el uso de la selección aleatoria de diseño de espacio de direcciones (ASLR).|
|[/ ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Informes de errores internos a Microsoft.|
|[/HEAP](../../build/reference/heap.md)|Establece el tamaño del montón de la imagen ejecutable en bytes.|
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Especifica si el archivo DLL o una imagen ejecutable es compatible con alta entropía (64 bits) dirección espacio selección aleatoria del diseño (ASLR).|
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Especifica si se comprueba la firma digital en tiempo de carga.|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Especifica si el objeto admite las direcciones que están más de dos gigabytes.|
|[/NOLOGO](../../build/reference/nologo-editbin.md)|Suprime la pancarta de inicio EDITBIN.|
|[/NXCOMPAT](../../build/reference/nxcompat.md)|Especifica si la imagen ejecutable es compatible con la prevención de ejecución de datos de Windows.|
|[/REBASE](../../build/reference/rebase.md)|Establece las direcciones base para los objetos especificados.|
|[/RELEASE](../../build/reference/release.md)|Establece la suma de comprobación en el encabezado.|
|[/SECTION](../../build/reference/section-editbin.md)|Invalida los atributos de una sección.|
|[/STACK](../../build/reference/stack.md)|Establece el tamaño de pila de la imagen ejecutable en bytes.|
|[/SUBSYSTEM](../../build/reference/subsystem.md)|Especifica el entorno de ejecución.|
|[/SWAPRUN](../../build/reference/swaprun.md)|Especifica que la imagen ejecutable debe copiar en el archivo de intercambio y, a continuación, ejecute desde allí.|
|[/TSAWARE](../../build/reference/tsaware.md)|Especifica que la aplicación está diseñada para ejecutarse en un entorno multiusuario.|
|[/VERSION](../../build/reference/version.md)|Establece el número de versión en el encabezado.|

## <a name="see-also"></a>Vea también

[Herramientas de compilación de C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
[Referencia de EDITBIN](../../build/reference/editbin-reference.md)