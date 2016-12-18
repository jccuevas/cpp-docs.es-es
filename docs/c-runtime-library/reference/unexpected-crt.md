---
title: "unexpected (CRT) | Microsoft Docs"
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
  - "unexpected"
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
apitype: "DLLExport"
f1_keywords: 
  - "unexpected"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "función inesperada"
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unexpected (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las llamadas `terminate` o funcionan se especifican mediante `set_unexpected`.  
  
## Sintaxis  
  
```  
void unexpected( void );  
```  
  
## Comentarios  
 La rutina de `unexpected` no se usa con la implementación actual del control de excepciones de C\+\+.  llamadas `terminate` de`unexpected` de forma predeterminada.  Puede cambiar este comportamiento predeterminado escribiendo una función personalizada de finalización y llamando `set_unexpected` con el nombre de la función como argumento.  `unexpected` llama a la función última especificada como argumento a `set_unexpected`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`unexpected`|\<eh.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 [Clase de System::Exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx)  
  
## Vea también  
 [Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_set\_se\_translator](../../c-runtime-library/reference/set-se-translator.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)