---
title: "setjmp | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "setjmp"
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
  - "setjmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "programas [C++], estados de ahorro"
  - "estado actual"
  - "setjmp (función)"
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# setjmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Guarda el estado actual del programa.  
  
## Sintaxis  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### Parámetros  
 `env`  
 Variable en la que se almacena el entorno.  
  
## Valor devuelto  
 Devuelve 0 después de guardar el entorno de la pila.  Si `setjmp` devuelve como resultado de una llamada de `longjmp` , devuelve el argumento de `value` de `longjmp`, o si el argumento de `value` de `longjmp` es 0, `setjmp` devuelve 1.  No se devuelve ningún error.  
  
## Comentarios  
 La función de `setjmp` guarda un entorno de pila, que puede restaurar posteriormente, mediante `longjmp`.  Cuando se usa juntos, `setjmp` y `longjmp` proporcionan una manera de ejecutar un no local `goto`.  Se suelen utilizar para pasar el control de ejecución al código de control de errores o la recuperación en una rutina previamente denominada sin utilizar convenciones normales de llamada o return.  
  
 Una llamada a `setjmp` guarda el entorno de la pila actual en `env`.  Una llamada subsiguiente a `longjmp` restaura el entorno guardado y devuelve el control al punto justo después de la llamada correspondiente de `setjmp` .  Todas las variables \(excepto variables de registro\) que el control que recibe rutinario contienen valores que tenían cuando `longjmp` se llamó.  
  
 No es posible utilizar `setjmp` para saltar de código nativo a código administrado.  
  
 **Nota** `setjmp` y `longjmp` no admiten la semántica de objeto de C\+\+.  En los programas de C\+\+, utilice el mecanismo de control de excepciones de C\+\+.  
  
 Para obtener más información, vea [Mediante setjmp y longjmp](../../cpp/using-setjmp-longjmp.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`setjmp`|\<setjmp.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [\_fpreset](../../c-runtime-library/reference/fpreset.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [\_setjmp3](../../c-runtime-library/setjmp3.md)