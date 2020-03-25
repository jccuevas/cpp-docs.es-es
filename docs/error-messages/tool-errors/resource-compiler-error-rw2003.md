---
title: Error del compilador de recursos RW2003
ms.date: 11/04/2016
f1_keywords:
- RW2003
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
ms.openlocfilehash: 60e813fff46ebc015f281dfed99d2916ca0eb4bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190617"
---
# <a name="resource-compiler-error-rw2003"></a>Error del compilador de recursos RW2003

Error de generación

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. **Error: el archivo de recursos de mapa de bits no tiene el formato 3,00**

   Los mapas de bits que utilizan el formato de Windows versión 2.x no pueden utilizarse en archivos de recursos de la versión 3.x. El mapa de bits se debe volver a dibujar o convertir al formato 3. x.

1. **Error: DIB antiguo en el nombre de recurso. Pasarlo a través de SDKPAINT**

   Un mapa de bits independiente del dispositivo (DIB) en el recurso especificado no es compatible con el formato de Windows 3,0. El mapa de bits se debe volver a dibujar o convertir al formato 3. x.

1. **Error: el nombre de recurso del archivo de recursos no tiene el formato 3,00**

   Un icono o un cursor en el recurso especificado usó un formato de una versión anterior de Windows. El icono o el cursor se debe volver a dibujar o convertir al formato 3. x.

1. **Formato de encabezado DIB desconocido**

   El encabezado de mapa de bits no es una estructura BITMAPCOREHEADER o BITMAPINFOHEADER.

1. **No se puede inicializar la información de símbolos**

   Este error solo se produce en C++visual. La causa probable es que haya demasiados archivos abiertos o que no pueda abrir o escribir en los archivos de datos necesarios para C++ que Visual importe los símbolos en el script. Visual C++ intenta crear estos archivos en el directorio especificado por la variable de entorno **TMP** o el directorio actual si no se especifica ninguno.

1. **No se puede guardar la información de símbolos**

   Este error solo se produce en C++visual. La causa probable es que haya demasiados archivos abiertos o que no pueda cerrar o escribir en los archivos de datos necesarios para C++ que Visual importe los símbolos en el script. Visual C++ intenta usar estos archivos en el directorio especificado por la variable de entorno **TMP** o el directorio actual si no se especifica ninguno.

1. **El archivo de recursos de archivo de mapa de bits no tiene el formato 2,03**

   Un mapa de bits utilizó un formato anterior a la versión 2.03. El mapa de bits se debe convertir o volver a dibujar con el formato de la versión 3.00 o una posterior.

1. **Recurso demasiado grande**

   En Windows 3,1, un recurso no puede superar los 65000 bytes aproximadamente. Si el recurso lo hace, no podrá compilarlo con Visual C++ o el compilador de recursos de línea de comandos. Este límite no se aplica a los cursores, iconos, mapas de bits u otros recursos basados en archivos.

1. **El archivo de recursos no tiene el formato 3,00**

   Un cursor o un icono utilizó un formato anterior a la versión 3,00. El recurso se debe convertir o volver a dibujar con el formato de la versión 3,00 o posterior.

1. **No se puede abrir el archivo temporal**

   El compilador de recursos/Visual C++ no pudo abrir un archivo temporal. La causa probable es que no tenga permisos de escritura para el directorio o que el directorio no exista. El compilador de recursos/Visual C++ intenta usar estos archivos en el directorio especificado por la variable de entorno **TMP** o el directorio actual si no se especifica ninguno.
