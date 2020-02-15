---
title: Opciones de EDITBIN
description: Guía de referencia de las opciones de la línea de comandos de la utilidad Microsoft EDITBIN.
ms.date: 02/09/2020
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: c27172522ceabeccd06d7b957aa791edc49beec8
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257707"
---
# <a name="editbin-options"></a>Opciones de EDITBIN

Puede usar EDITBIN para modificar archivos objeto, archivos ejecutables y bibliotecas de vínculos dinámicos (dll). Las opciones especifican los cambios que realiza EDITBIN.

Una opción consta de un especificador de opción, que puede ser un guión (`-`) o una barra diagonal (`/`), seguido del nombre de la opción. Los nombres de opciones no se pueden abreviar. Algunas opciones toman los argumentos que se especifican después de dos puntos (`:`). No se permiten espacios ni tabulaciones dentro de una especificación de opción. Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos. Los nombres de opciones y sus argumentos de palabra clave o de nombre de archivo no distinguen mayúsculas de minúsculas. Por ejemplo, `-bind` y `/BIND` significan lo mismo.

EDITBIN tiene las siguientes opciones:

|Opción|Propósito|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Especifica si se puede enlazar un archivo DLL.|
|[/ALLOWISOLATION](allowisolation.md)|Especifica el comportamiento de búsqueda del manifiesto del archivo ejecutable o DLL.|
|[/APPCONTAINER](appcontainer.md)|Especifica si la aplicación se debe ejecutar dentro de un AppContainer, por ejemplo, una aplicación de UWP.|
|[/BIND](bind.md)|Establece las direcciones de los puntos de entrada de los objetos especificados para acelerar el tiempo de carga.|
|[/DYNAMICBASE](dynamicbase.md)|Especifica si el archivo DLL o la imagen ejecutable se pueden reorganizar aleatoriamente en tiempo de carga mediante la selección aleatoria del diseño del espacio de direcciones (ASLR).|
|[/ERRORREPORT](errorreport-editbin-exe.md)| En desuso. Los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
|[/HEAP](heap.md)|Establece el tamaño del montón de la imagen ejecutable en bytes.|
|[/HIGHENTROPYVA](highentropyva.md)|Especifica si el archivo DLL o la imagen ejecutable admite la selección aleatoria del diseño del espacio de direcciones (ASLR) de alta entropía (64 bits).|
|[/INTEGRITYCHECK](integritycheck.md)|Especifica si se debe comprobar la firma digital en el momento de la carga.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Especifica si el objeto admite direcciones de más de dos gigabytes.|
|[/NOLOGO](nologo-editbin.md)|Suprime la pancarta de inicio de EDITBIN.|
|[/NXCOMPAT](nxcompat.md)|Especifica si la imagen ejecutable es compatible con la prevención de ejecución de datos de Windows.|
|[/REBASE](rebase.md)|Establece las direcciones base de los objetos especificados.|
|[/RELEASE](release.md)|Establece la suma de comprobación en el encabezado.|
|[/SECTION](section-editbin.md)|Invalida los atributos de una sección.|
|[/STACK](stack.md)|Establece el tamaño de la pila de la imagen ejecutable en bytes.|
|[/SUBSYSTEM](subsystem.md)|Especifica el entorno de ejecución.|
|[/SWAPRUN](swaprun.md)|Especifica que la imagen ejecutable se copia en el archivo de intercambio y, a continuación, se ejecuta desde allí.|
|[/TSAWARE](tsaware.md)|Especifica que la aplicación está diseñada para ejecutarse en un entorno de varios usuarios.|
|[/VERSION](version.md)|Establece el número de versión en el encabezado.|

## <a name="see-also"></a>Consulte también

\ [adicionales de herramientas de compilación de MSVC](c-cpp-build-tools.md)
[Referencia de EDITBIN](editbin-reference.md)
