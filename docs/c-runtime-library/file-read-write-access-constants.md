---
title: "Constantes de acceso de lectura y escritura de archivos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.constants.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "constantes de acceso de lectura y escritura de archivos"
  - "constantes [C++], atributos de archivo"
  - "constantes de acceso de lectura y escritura de archivos"
  - "constantes de acceso de lectura y escritura"
  - "constantes de acceso de escritura"
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Constantes de acceso de lectura y escritura de archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <stdio.h>  
```  
  
## Comentarios  
 Estas constantes especifican el tipo de acceso \(“a”, “r”, o “w”\) solicitados para el archivo.  [de modalidad de traducción](../c-runtime-library/file-translation-constants.md) \(“b” o “t”\) y [modo de confirmación\-a\- disco](../c-runtime-library/commit-to-disk-constants.md) \(“c” o “n”\) se pueden especificar con el tipo de acceso.  
  
 Los tipos de acceso se describen a continuación.  
  
 **"a"**  
 Abrir para escribir al final del archivo \(el anexar\); crea el archivo primero si no existe.  Todas las operaciones de escritura aparecen al final del archivo.  Aunque el puntero de archivo se puede cambiar de posición mediante `fseek` o **rewind**, se mueve siempre al final del archivo antes de que se realice cualquier operación de escritura.  
  
 **"a\+"**  
 Como anteriormente, pero también permite la lectura.  
  
 **"r"**  
 Abre para lectura.  Si el archivo no existe o no se encuentra, la llamada a abrir el archivo producirá un error.  
  
 **"r\+"**  
 Abre para lectura y escritura.  Si el archivo no existe o no se encuentra, la llamada a abrir el archivo producirá un error.  
  
 **"w"**  
 Abre un archivo vacío para escritura.  Si el archivo especificado existe, se destruye su contenido.  
  
 **"w\+"**  
 Abre un archivo vacío para lectura y escritura.  Si el archivo especificado existe, se destruye su contenido.  
  
 Cuando se especifica la “R\+”, “w\+ el tipo”, o “a\+”, se permiten la lectura y escritura \(el archivo se abre para “update”\).  Sin embargo, cuando cambie de lectura y escritura, debe haber `fflush`intermedia, `fsetpos`, `fseek`, u operación de **rewind** .  La posición actual se puede especificar para la operación de `fsetpos` o de `fseek` .  
  
## Vea también  
 [\_fdopen, \_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, \_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, \_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_fsopen, \_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [\_popen, \_wpopen](../c-runtime-library/reference/popen-wpopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)