---
title: "L&#237;nea de comandos de BSCMAKE | Microsoft Docs"
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
  - "BSCMAKE, línea de comandos"
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# L&#237;nea de comandos de BSCMAKE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para ejecutar BSCMAKE se utiliza la siguiente sintaxis de línea de comandos:  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 Las opciones sólo pueden aparecer en el campo `options` de la línea de comandos.  
  
 El campo *sbrfiles* especifica uno o más archivos .sbr creados mediante un compilador o un ensamblador.  Los nombres de los archivos .sbr se han de separar con espacios o tabulaciones.  Se debe especificar la extensión; no existe una extensión predeterminada.  Se puede especificar una ruta de acceso con el nombre del archivo y se pueden utilizar comodines del sistema operativo \(\* y ?\).  
  
 Durante una compilación incremental se pueden especificar nuevos archivos .sbr que no formaron parte de la compilación original.  Si se desea que todas las contribuciones se mantengan en el archivo de información de examen, hay que especificar todos los archivos .sbr \(incluidos los archivos truncados\) que se usaron originalmente para crear el archivo .bsc.  Si se omite un archivo .sbr, se quita la contribución que aporta al archivo de información de examen.  
  
 No se puede especificar un archivo .sbr truncado para una compilación completa.  Una compilación completa requiere contribuciones de todos los archivos .sbr especificados.  Antes de realizar una generación completa, se ha de volver a compilar el proyecto y crear un nuevo archivo .sbr para cada archivo vacío.  
  
 El comando siguiente ejecuta BSCMAKE para compilar un archivo denominado MAIN.bsc a partir de tres archivos .sbr:  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 Para obtener información relacionada, vea [Archivo de comandos de BSCMAKE](../../build/reference/bscmake-command-file-response-file.md) y [Opciones de BSCMAKE](../../build/reference/bscmake-options.md).  
  
## Vea también  
 [Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)