---
title: "_unlock_file | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_unlock_file"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_unlock_file"
  - "unlock_file"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_unlock_file (función)"
  - "archivos [C++], desbloquear"
  - "unlock_file (función)"
  - "desbloquear archivos"
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _unlock_file
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Desbloquea un archivo, lo que otros procesos tengan acceso al archivo.  
  
## Sintaxis  
  
```  
void _unlock_file(  
   FILE* file  
);  
```  
  
#### Parámetros  
 `file`  
 Identificador de archivos.  
  
## Comentarios  
 La función de `_unlock_file` desbloquea el archivo especificado por `file`.  Desbloquear un archivo permite el acceso al archivo por otros procesos.  Esta función no se debería llamar a menos que `_lock_file` previamente fuera en el puntero de `file` .  La llamada `_unlock_file` en un archivo que no está bloqueado puede producir un interbloqueo.  Para obtener un ejemplo, vea [\_lock\_file](../../c-runtime-library/reference/lock-file.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_unlock_file`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 [System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_lock\_file](../../c-runtime-library/reference/lock-file.md)