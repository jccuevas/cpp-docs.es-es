---
title: Error del compilador de recursos RW2003 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2003
dev_langs:
- C++
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7b4341c4567e7a58135cc99a793f287f810043
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096787"
---
# <a name="resource-compiler-error-rw2003"></a>Error del compilador de recursos RW2003

Error de generación

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. **Error: Archivo de recursos de mapa de bits archivo no está en formato 3.00**

     Los mapas de bits que utilizan el formato de Windows versión 2.x no pueden utilizarse en archivos de recursos de la versión 3.x. El mapa de bits debe ser vuelve a dibujar o convertir a formato 3.x.

1. **Error: DIB antiguo en el nombre del recurso. Pasarlo a través de SDKPAINT**

     Un mapa de bits independiente del dispositivo (DIB) en el recurso especificado no es compatible con el formato de Windows 3.0. El mapa de bits se debe dibujar o convertir al formato 3.x.

1. **Error: Recursos-nombre de archivo de recursos no está en formato 3.00**

     Un icono o cursor en el recurso especificado utiliza un formato de una versión anterior de Windows. El nuevo icono o cursor debe ser convertir al formato 3.x o vuelve a dibujar.

1. **formato de encabezado DIB desconocido**

     El encabezado de mapa de bits no es una estructura BITMAPCOREHEADER o BITMAPINFOHEADER.

1. **No se puede inicializar la información de símbolos**

     Este error se produce solo en Visual C++. La causa probable es que haya demasiados archivos abiertos o no se puede abrir o escribir en los archivos de datos necesarios para que importar los símbolos en el script de Visual C++. Visual C++ intenta crear estos archivos en el directorio especificado por el **TMP** variable de entorno o el directorio actual si se especifica ninguno.

1. **No se puede guardar la información de símbolos**

     Este error se produce solo en Visual C++. La causa probable es que haya demasiados archivos abiertos o no se puede cerrar o escribir en los archivos de datos necesarios para que importar los símbolos en el script de Visual C++. Visual C++ intenta usar estos archivos en el directorio especificado por el **TMP** variable de entorno o el directorio actual si se especifica ninguno.

1. **Archivo de recursos del archivo de mapa de bits no está en formato 2.03**

     Un mapa de bits utilizó un formato anterior a la versión 2.03. El mapa de bits se debe convertir o volver a dibujar con el formato de la versión 3.00 o una posterior.

1. **Recurso demasiado grande**

     Para Windows 3.1 un recurso no puede superar los 65000 bytes aproximadamente. Si hace el recurso, a continuación, no podrá compilar con Visual C++ o el compilador de recursos de línea de comandos. Este límite no se aplica a los cursores, iconos, mapas de bits u otros recursos basados en archivos.

9. **Archivo de recursos no está en formato 3.00**

     Un icono o cursor utilizó un formato anterior a la versión 3.00. El recurso se debe convertir o volver a dibujar con el formato para la versión 3.00 o posterior.

10. **No se puede abrir el archivo temporal**

     El compilador de recursos/Visual C++ no pudo abrir un archivo temporal. La causa probable es que no tiene permisos de escritura para el directorio o el directorio no existe. El compilador de recursos/Visual C++ intenta usar estos archivos en el directorio especificado por la variable de entorno **TMP** o el directorio actual si no se especifica ninguno.