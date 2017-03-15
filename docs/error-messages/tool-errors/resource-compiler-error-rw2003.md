---
title: "Error del compilador de recursos RW2003 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2003"
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador de recursos RW2003
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Error de generación  
  
### Posibles causas del error:  
  
1.  **Error: el archivo de recursos del archivo de mapa de bits no está en formato 3.00**  
  
     Los mapas de bits en formato de la versión 2.x de Windows no se pueden usar en los archivos de recursos de la versión 3.x.  El mapa de bits se debe volver a dibujar o reconvertir al formato 3.x.  
  
2.  **Error: DIB antiguo en el nombre de recurso.  Pasarlo a través de SDKPAINT**  
  
     Un Mapa de bits independiente de dispositivo \(DIB\) en el recurso especificado no es compatible con el formato 3.0 de Windows.  El mapa de bits se debe volver a dibujar o convertir al formato 3.x.  
  
3.  **Error: el nombre de recurso del archivo de recursos no está en formato 3.00**  
  
     Un icono o un cursor en el recurso especificado utiliza un formato de una versión anterior de Windows.  El icono o el cursor se debe volver a dibujar o convertir al formato 3.x.  
  
4.  **Formato de encabezado DIB desconocido**  
  
     El encabezado de mapa de bits no es una estructura BITMAPCOREHEADER o BITMAPINFOHEADER.  
  
5.  **No se puede inicializar la información de símbolos**  
  
     Este error sólo aparece en Visual C\+\+.  La causa probable es que haya demasiados archivos abiertos o no se puedan abrir o escribir en los archivos de datos necesarios para que Visual C\+\+ importe los símbolos en el script.  Visual C\+\+ intenta crear estos archivos en el directorio especificado por la variable de entorno **TMP o el directorio actual si no se especifica ninguno.**  
  
6.  **No se puede guardar la información de símbolos**  
  
     Este error sólo aparece en Visual C\+\+.  La causa probable es que haya demasiados archivos abiertos o no se puedan cerrar o escribir en los archivos de datos necesarios para que Visual C\+\+ importe los símbolos en el script.  Visual C\+\+ intenta usar estos archivos en el directorio especificado por la variable de entorno **TMP o el directorio actual si no se especifica ninguno.**  
  
7.  **El archivo de recursos del archivo de mapa de bits no está en formato 2.03**  
  
     Un mapa de bits utilizó un formato anterior a la versión 2.03.  El mapa de bits se debe convertir o volver a dibujar utilizando el formato para la versión 3.00 o posterior.  
  
8.  **Recurso demasiado grande**  
  
     Para Windows 3.1 un recurso no puede superar los 65000 bytes aproximadamente.  Si el recurso los supera, entonces no se podrá compilar con Visual C\+\+ o con el compilador de recursos de línea de comandos.  Este límite no se aplica a cursores, iconos, mapas de bits u otros recursos basados en archivos.  
  
9. **El archivo de recursos no está en formato 3.00**  
  
     Un cursor o un icono ha utilizado un formato anterior a la versión 3.00.  El recurso se debe convertir o volver a dibujar usando el formato para la versión 3.00 o posterior.  
  
10. **No se puede abrir un archivo temporal**  
  
     El compilador de recursos\/Visual C\+\+ no pudo abrir un archivo temporal.  La causa puede ser que no se tengan permisos de escritura para el directorio, o que el directorio no exista.  El compilador de recursos\/Visual C\+\+ intenta usar estos archivos en el directorio especificado por la variable de entorno **TMP o el directorio actual si no se especifica ninguno.**