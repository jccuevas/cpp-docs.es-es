---
title: Opciones de EDITBIN | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1922e410b0151337ce403e24d20ae90b7e964cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="editbin-options"></a>Opciones de EDITBIN
Puede utilizar EDITBIN para modificar archivos objeto, archivos ejecutables y bibliotecas de vínculos dinámicos (DLL). Opciones especifican los cambios que realiza EDITBIN.  
  
 Una opción consta de un especificador de opción, que es un guión (-) o una barra diagonal (/), seguido del nombre de la opción. Los nombres de opción no pueden abreviarse. Algunas opciones toman argumentos que se especifican precedidos de dos puntos (:). No se permiten espacios ni tabulaciones dentro de una especificación de opción. Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos. Los nombres de opción y sus argumentos de palabra clave o argumentos de nombre de archivo no distinguen mayúsculas de minúsculas. Por ejemplo, - bind y /BIND significan lo mismo.  
  
 EDITBIN tiene las siguientes opciones:  
  
|Opción|Propósito|  
|------------|-------------|  
|[/ALLOWBIND](../../build/reference/allowbind.md)|Especifica si se puede enlazar un archivo DLL.|  
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|Especifica el archivo DLL o el comportamiento de búsqueda de manifiesto del archivo ejecutable.|  
|[/APPCONTAINER](../../build/reference/appcontainer.md)|Especifica si la aplicación se debe ejecutar dentro de un AppContainer: por ejemplo, una aplicación de UWP.|  
|[/BIND](../../build/reference/bind.md)|Establece las direcciones de los puntos de entrada en los objetos especificados para acelerar el tiempo de carga.|  
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|Especifica si el archivo DLL o una imagen ejecutable puede ser reorganizar aleatoriamente en tiempo de carga mediante el uso de selección aleatoria de diseño de espacio de direcciones (ASLR).|  
|[/ ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Informes de errores internos a Microsoft.|  
|[/HEAP](../../build/reference/heap.md)|Establece el tamaño del montón de la imagen ejecutable en bytes.|  
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Especifica si el archivo DLL o una imagen ejecutable admite selección aleatoria de alta entropía direcciones (64 bits) espacio diseño (ASLR).|  
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Especifica si se debe comprobar la firma digital en tiempo de carga.|  
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Especifica si el objeto admite direcciones que sean más de dos gigabytes.|  
|[/ NOLOGO](../../build/reference/nologo-editbin.md)|Suprime la pancarta de inicio EDITBIN.|  
|[/NXCOMPAT](../../build/reference/nxcompat.md)|Especifica si la imagen ejecutable es compatible con la prevención de ejecución de datos de Windows.|  
|[/REBASE](../../build/reference/rebase.md)|Establece las direcciones base para los objetos especificados.|  
|[/RELEASE](../../build/reference/release.md)|Establece la suma de comprobación en el encabezado.|  
|[/ SECCIÓN](../../build/reference/section-editbin.md)|Invalida los atributos de una sección.|  
|[/STACK](../../build/reference/stack.md)|Establece el tamaño de pila de la imagen ejecutable en bytes.|  
|[/SUBSYSTEM](../../build/reference/subsystem.md)|Especifica el entorno de ejecución.|  
|[/SWAPRUN](../../build/reference/swaprun.md)|Especifica que la imagen ejecutable debe copiar en el archivo de intercambio y, a continuación, ejecute desde ahí.|  
|[/TSAWARE](../../build/reference/tsaware.md)|Especifica que la aplicación está diseñada para ejecutarse en un entorno multiusuario.|  
|[/VERSION](../../build/reference/version.md)|Establece el número de versión en el encabezado.|  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de compilación de C/c ++](../../build/reference/c-cpp-build-tools.md)   
 [Referencia de EDITBIN](../../build/reference/editbin-reference.md)