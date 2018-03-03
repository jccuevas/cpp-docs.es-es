---
title: Error del compilador de recursos RW2003 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW2003
dev_langs:
- C++
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f388ca21d95e7d675a6b9890a7368765b5c0d7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rw2003"></a>Error del compilador de recursos RW2003
Error de generación  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  **Error: Archivo de recursos de archivo mapa de bits no tiene formato 3.00**  
  
     Los mapas de bits que utilizan el formato de Windows versión 2.x no pueden utilizarse en archivos de recursos de la versión 3.x. El mapa de bits debe ser vuelve a dibujarse o convertir al formato 3.x.  
  
2.  **Error: DIB antiguo en el nombre del recurso. Pasar a través de SDKPAINT**  
  
     Un mapa de bits independiente del dispositivo (DIB) en el recurso especificado no es compatible con el formato de Windows 3.0. El mapa de bits debe ser vuelve a dibujarse o convertir al formato 3.x.  
  
3.  **Error: Archivo-nombre del recurso no está en formato 3.00**  
  
     Un icono o cursor en el recurso especificado ha utilizado un formato de una versión anterior de Windows. El nuevo icono o cursor debe vuelve a dibujarse o convertir al formato 3.x.  
  
4.  **Formato de encabezado DIB desconocido**  
  
     El encabezado de mapa de bits no es una estructura BITMAPCOREHEADER o BITMAPINFOHEADER.  
  
5.  **No se puede inicializar la información de símbolos**  
  
     Este error se produce solo en Visual C++. La causa probable es que haya demasiados archivos abiertos o no se puede abrir o escribir en los archivos de datos necesarios para que Visual C++ importe los símbolos en el script. Visual C++ intenta crear estos archivos en el directorio especificado por la **TMP** variable de entorno o el directorio actual si no se especifica ninguno.  
  
6.  **No se puede guardar información de símbolos**  
  
     Este error se produce solo en Visual C++. La causa probable es que haya demasiados archivos abiertos o no se puede cerrar o escribir en los archivos de datos necesarios para que Visual C++ importe los símbolos en el script. Visual C++ intenta usar estos archivos en el directorio especificado por la **TMP** variable de entorno o el directorio actual si no se especifica ninguno.  
  
7.  **Archivo de recursos de archivo de mapa de bits no tiene formato 2.03**  
  
     Un mapa de bits utilizó un formato anterior a la versión 2.03. El mapa de bits se debe convertir o volver a dibujar con el formato de la versión 3.00 o una posterior.  
  
8.  **Recurso demasiado grande**  
  
     Para Windows 3.1 un recurso no puede superar los 65000 bytes aproximadamente. Si el recurso existe, a continuación, no podrá compilar con Visual C++ o el compilador de recursos de línea de comandos. Este límite no se aplica a los cursores, iconos, mapas de bits u otros recursos basados en archivos.  
  
9. **Archivo de recursos no está en formato 3.00**  
  
     Un icono o cursor utilizó un formato anterior a la versión 3.00. El recurso se debe convertir o volver a dibujar con el formato para la versión 3.00 o posterior.  
  
10. **No se puede abrir el archivo temporal**  
  
     El compilador de recursos/Visual C++ no pudo abrir un archivo temporal. La causa probable es que no tiene permisos de escritura para el directorio o que el directorio no existe. El compilador de recursos/Visual C++ intenta usar estos archivos en el directorio especificado por la variable de entorno **TMP** o el directorio actual si no se especifica ninguno.