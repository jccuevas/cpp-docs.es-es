---
title: "_CrtCheckMemory | Microsoft Docs"
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
  - "_CrtCheckMemory"
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
  - "CrtCheckMemory"
  - "_CrtCheckMemory"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtCheckMemory (función)"
  - "CrtCheckMemory (función)"
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtCheckMemory
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Confirma la integridad de los bloques de memoria asignados en el montón de depuración \(solo versión de depuración\).  
  
## Sintaxis  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## Valor devuelto  
 Si se ejecuta correctamente, `_CrtCheckMemory` devuelve TRUE; de lo contrario, la función devuelve FALSE.  
  
## Comentarios  
 La función `_CrtCheckMemory` valida la memoria asignada por el administrador del montón de depuración comprobando el montón base subyacente e inspeccionando cada bloque de memoria.  Si se encuentra un error o una inconsistencia de memoria en el montón base subyacente, la información de encabezado de depuración o los búferes de sobrescritura, `_CrtCheckMemory` genera un informe de depuración en el que se describe la condición de error.  Cuando no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtCheckMemory` se quitan durante el preprocesamiento.  
  
 El comportamiento de `_CrtCheckMemory` se puede controlar estableciendo los campos de bits del marcador [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) mediante la función [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md).  Si se activa el campo de bits **\_CRTDBG\_CHECK\_ALWAYS\_DF**, se llama a `_CrtCheckMemory` cada vez que se solicita una operación de asignación de memoria.  Aunque este método ralentiza la ejecución, es útil para detectar errores rápidamente.  Si se desactiva el campo de bits `_CrtCheckMemory`, **\_CRTDBG\_ALLOC\_MEM\_DF** no comprueba el montón y devuelve inmediatamente el valor **TRUE**.  
  
 Dado que esta función devuelve **TRUE** o **FALSE**, se puede pasar a una de las macros de [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración.  En el ejemplo siguiente se genera un error de aserción si se detectan daños en el montón:  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 Para obtener más información sobre cómo se puede usar `_CrtCheckMemory` con otras funciones de depuración, vea [Funciones que indican el estado del montón](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions).  Para obtener información general sobre la administración de memoria y el montón de depuración, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtCheckMemory`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtCheckMemory`, vea [crt\_dbg1](http://msdn.microsoft.com/es-es/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## Equivalente en .NET Framework  
 [System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)