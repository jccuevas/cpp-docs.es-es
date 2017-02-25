---
title: "Llamadas del sistema | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.system"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "llamadas al sistema"
  - "Windows [C++], llamadas al sistema"
ms.assetid: 0255f2ec-a5a0-487e-8b09-9dad001d81ed
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Llamadas del sistema
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las funciones siguientes son llamadas del sistema operativo Windows.  
  
### Funciones de llamada del sistema  
  
|Función|Utilice|Equivalente de .NET Framework|  
|-------------|-------------|-----------------------------------|  
|[\_findclose](../c-runtime-library/reference/findclose.md)|Recursos de lanzamiento de operaciones anteriores de búsqueda|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_findfirst, \_findfirst32, \_findfirst64, \_findfirsti64, \_findfirst32i64, \_findfirst64i32, \_wfindfirst, \_wfindfirst32, \_wfindfirst64, \_wfindfirsti64, \_wfindfirst32i64, \_wfindfirst64i32](../c-runtime-library/reference/findfirst-functions.md)|Archivo de búsqueda con atributos especificados|[\<caps:sentence id\="tgt12" sentenceid\="e22cfa910fbeac637b6aba4ed3f9dc48" class\="tgtSentence"\>System::IO::DirectoryInfo::GetFiles\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.getfiles.aspx)|  
|[\_findnext, \_findnext32, \_findnext64, \_findnexti64, \_findnext32i64, \_findnext64i32, \_wfindnext, \_wfindnext32, \_wfindnexti64, \_wfindnext64, \_wfindnexti64](../c-runtime-library/reference/findnext-functions.md)|El siguiente archivo de búsqueda con atributos especificados|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Control de archivos](../c-runtime-library/file-handling.md)   
 [Control de directorio](../c-runtime-library/directory-control.md)   
 [E\/S de bajo nivel](../c-runtime-library/low-level-i-o.md)