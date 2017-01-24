---
title: "longjmp | Microsoft Docs"
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
  - "longjmp"
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
  - "longjmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "longjmp (función)"
  - "restaurar entorno de pila y configuración regional de ejecución"
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# longjmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Restaura el entorno de la pila y la configuración regional de la ejecución.  
  
## Sintaxis  
  
```  
  
      void longjmp(  
   jmp_buf env,  
   int value   
);  
```  
  
#### Parámetros  
 `env`  
 Variable en la que se almacena el entorno.  
  
 *valor*  
 Valor que va a la llamada de `setjmp` .  
  
## Comentarios  
 La función de `longjmp` restaurar un entorno de pila y configuración regional de ejecución guardada previamente en `env` por `setjmp`.  `setjmp` y `longjmp` proporcionan una manera de ejecutar `goto`local; se suelen utilizar para pasar el control de ejecución al código de control de errores o la recuperación en una rutina previamente denominada sin utilizar convenciones normales de llamada y return.  
  
 Una llamada a `setjmp` hace que el entorno de la pila actual que se guardará en `env`.  Una llamada subsiguiente a `longjmp` restaura el entorno guardado y devuelve el control al punto inmediatamente después de la llamada correspondiente de `setjmp` .  La ejecución se reanuda como si *el valor* acababa de ser devuelto por la llamada de `setjmp` .  Los valores de todas las variables \(excepto variables de registro\) que es accesible al control que recibe rutinario contienen valores que tenían cuando `longjmp` se llamó.  Los valores de las variables de registro son imprevisibles.  El valor devuelto por `setjmp` debe ser cero.  Si se pasa *el valor* como 0, el valor 1 se sustituye en la devolución real.  
  
 Llame a `longjmp` antes de la función que llamó `setjmp` vuelve; si no los resultados son imprevisibles.  
  
 Observe las restricciones siguientes al utilizar `longjmp`:  
  
-   No suponga que los valores de las variables de registro seguirán siendo iguales.  Los valores de las variables de registro en `setjmp` que llama rutinario no se pueden restaurar los valores adecuados después de ejecutar `longjmp` .  
  
-   No utilice `longjmp` para transferir el control fuera de una rutina interrupción\- que administra a menos que la interrupción se produjo por una excepción flotante.  En este caso, un programa puede volver de un controlador de interrupción mediante `longjmp` si primero se reinicializa el paquete de software matemáticos flotante llamando a `_fpreset`.  
  
     **Nota** Tenga cuidado al utilizar `setjmp` y `longjmp` en programas de C\+\+.  Dado que estas funciones no admiten la semántica de objeto de C\+\+, es más seguro utilizar el mecanismo de control de excepciones de C\+\+.  
  
 Para obtener más información, vea [Mediante setjmp y longjmp](../../cpp/using-setjmp-longjmp.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`longjmp`|\<setjmp.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Vea el ejemplo para [\_fpreset](../../c-runtime-library/reference/fpreset.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [setjmp](../../c-runtime-library/reference/setjmp.md)