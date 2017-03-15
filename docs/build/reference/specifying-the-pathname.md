---
title: "Especificar la ruta de acceso | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), archivos de salida"
  - "nombres [C++], archivos de resultados del compilador"
  - "archivos de salida, especificar nombres de rutas de acceso"
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Especificar la ruta de acceso
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las opciones del archivo de salida aceptan un argumento *pathname* que puede especificar una ubicación y un nombre para el archivo de salida.  El argumento puede incluir un nombre de unidad, un directorio y un nombre de archivo.  No se permite un espacio entre la opción y el argumento.  
  
 Si *pathname* incluye un nombre de archivo sin extensión, el compilador asigna al resultado una extensión predeterminada.  Si *pathname* incluye un directorio, pero no un nombre de archivo, el compilador crea un archivo con un nombre predeterminado en el directorio especificado.  El nombre predeterminado se compone del nombre base del archivo de código fuente y una extensión predeterminada que depende del tipo de archivo de salida.  Si omite completamente *pathname*, el compilador crea un archivo con un nombre predeterminado en un directorio predeterminado.  
  
 De forma alternativa, el argumento *pathname* puede ser un nombre de dispositivo \(AUX, CON, PRN o NUL\) en lugar de un nombre de archivo.  No use un espacio entre la opción y el nombre de dispositivo ni un signo de dos puntos como parte del nombre del dispositivo.  
  
|Nombre del dispositivo|Representa|  
|----------------------------|----------------|  
|AUX|Dispositivo auxiliar|  
|CON|Consola|  
|PRN|Impresora|  
|NUL|Dispositivo nulo \(no se crea un archivo\)|  
  
## Ejemplo  
 La línea de comandos siguiente envía un archivo de asignaciones a la impresora:  
  
```  
CL /FmPRN HELLO.CPP  
```  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)