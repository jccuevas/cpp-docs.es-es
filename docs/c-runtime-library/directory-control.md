---
title: "Control de directorio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.programs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "controles [C++], directorio"
  - "rutinas de control de directorio"
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Control de directorio
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas rutinas tienen acceso, modificar, y obtienen a información sobre la estructura de directorios.  
  
### Rutinas de la Directorio\-CONTROL  
  
|Rutina|Utilice|Equivalente de .NET Framework|  
|------------|-------------|-----------------------------------|  
|[\_chdir, \_wchdir](../c-runtime-library/reference/chdir-wchdir.md)|Directorio de trabajo actual de cambio|[\<caps:sentence id\="tgt8" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_chdrive](../c-runtime-library/reference/chdrive.md)|Unidad actual de cambio|[\<caps:sentence id\="tgt11" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_getcwd, \_wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|Obtiene el directorio de trabajo actual para la unidad predeterminada|[\<caps:sentence id\="tgt14" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_getdcwd, \_wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|Obtiene el directorio de trabajo actual para la unidad especificada|[\<caps:sentence id\="tgt16" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|Rellena una estructura de `_diskfree_t` con información sobre una unidad de disco.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_getdrive](../c-runtime-library/reference/getdrive.md)|Obtenga la unidad \(predeterminada\) actual|[\<caps:sentence id\="tgt23" sentenceid\="6aacc5c9471c794e236850e17f3f1787" class\="tgtSentence"\>System::Environment::CurrentDirectory\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)|  
|[\_getdrives](../c-runtime-library/reference/getdrives.md)|Devuelve una máscara de bits que representa las unidades de disco disponibles actualmente.|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_mkdir, \_wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|Haga el nuevo directorio|[System::IO::Directory::CreateDirectory](https://msdn.microsoft.com/en-us/library/system.io.directory.createdirectory.aspx), [System::IO::DirectoryInfo::CreateSubdirectory](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.createsubdirectory.aspx)|  
|[\_rmdir, \_wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|Quitar directorio|[\<caps:sentence id\="tgt32" sentenceid\="de5c5e84e86fdd3cd99296d3b2518f57" class\="tgtSentence"\>System::IO::Directory::Delete\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.directory.delete.aspx)|  
|[\_searchenv, \_wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md), [\_searchenv\_s, \_wsearchenv\_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Buscar el archivo dado en las rutas de acceso especificadas|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Control de archivos](../c-runtime-library/file-handling.md)   
 [Llamadas del sistema](../c-runtime-library/system-calls.md)