---
title: "Manipulaci&#243;n del b&#250;fer | Microsoft Docs"
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
  - "c.memory"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "búferes"
  - "búferes, rutinas de manipulación"
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Manipulaci&#243;n del b&#250;fer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice estas rutinas para trabajar con áreas de memoria de byte\-por\- byte.  
  
### Rutinas de la Búfer\-manipulación  
  
|Rutina|Utilice|Equivalente de .NET Framework|  
|------------|-------------|-----------------------------------|  
|[\_memccpy](../c-runtime-library/reference/memccpy.md)|Copie los caracteres a partir de un búfer a otro hasta el carácter dado o se ha copiado el número de caracteres especificado|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx), [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)|  
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Puntero de vuelta a la primera aparición, dentro del número de caracteres especificado, de carácter dado en búfer|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Compare especifica el número de caracteres de dos búferes|[System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx), [System::String::Equals](https://msdn.microsoft.com/en-us/library/system.string.equals.aspx)|  
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy\_s, wmemcpy\_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Copie el número de caracteres especificado a partir de un búfer a otro|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx), [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)|  
|[\_memicmp, \_memicmp\_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Compare especifica el número de caracteres de dos búferes sin tener en cuenta el caso|[System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx), [System::String::Equals](https://msdn.microsoft.com/en-us/library/system.string.equals.aspx)|  
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove\_s, wmemmove\_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Copie el número de caracteres especificado a partir de un búfer a otro|[\<caps:sentence id\="tgt21" sentenceid\="3833f84fafc5c85a0cac972319a7142c" class\="tgtSentence"\>System::Buffer::BlockCopy\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)|  
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Utilice el carácter especificado para inicializar número de bytes especificado en el búfer|[\<caps:sentence id\="tgt23" sentenceid\="b681ccb0db940e3c31a14bf4b7e7aaf8" class\="tgtSentence"\>System::Buffer::SetByte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.buffer.setbyte.aspx)|  
|[\_swab](../c-runtime-library/reference/swab.md)|Cambie los bytes de datos y almacénelos en la ubicación especificada|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
 Cuando el origen y las áreas objetivo se superponen, sólo `memmove` se garantiza para copiar el origen completo correctamente.  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)