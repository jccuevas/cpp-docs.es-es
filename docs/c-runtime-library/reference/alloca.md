---
title: "_alloca | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_alloca"
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
  - "_alloca"
  - "alloca"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_alloca (función)"
  - "alloca (función)"
  - "asignación de memoria, pila"
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _alloca
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna memoria en la pila.  Se deja de utilizar esta función porque una versión más segura está disponible; vea [\_malloca](../../c-runtime-library/reference/malloca.md).  
  
## Sintaxis  
  
```  
void *_alloca(   
   size_t size   
);  
```  
  
#### Parámetros  
 \[in\] `size`  
 Bytes que se afectarán asignado de la pila.  
  
## Valor devuelto  
 La rutina de `_alloca` devuelve un puntero de `void` el espacio asignado, que se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Si `size` es 0, `_alloca` asigna un elemento de la cero\- longitud y devuelve un puntero válido a ese elemento.  
  
 Se genera una excepción de desbordamiento de pila si el espacio no puede estar asignado.  La excepción de desbordamiento de pila no es excepción de c\+\+.; es una excepción estructurada.  En lugar de utilizar el control de excepciones de C\+\+, debe utilizar [Control de excepciones estructurado](../../cpp/structured-exception-handling-c-cpp.md) \(SEH\).  
  
## Comentarios  
 `_alloca` asigna los bytes de `size` de la pila del programa.  El espacio asignado automáticamente se libera cuando finaliza la función de llamada \(no cuando la asignación pasa simplemente fuera de ámbito\).  Por consiguiente, no pase el valor devuelto del puntero en `_alloca` como argumento a [libre](../../c-runtime-library/reference/free.md).  
  
 Hay restricciones explícitamente a `_alloca` en un controlador de excepciones \(EH\).  Las rutinas de EH que se ejecutan en procesadores de x86\-class funcionan en su propio cuadro de memoria: Realizan las tareas en el espacio de memoria que no se basa en la ubicación actual del puntero de pila de la función envolvente.  Las implementaciones más comunes incluyen expresiones de control estructurado de excepciones \(SEH\) de windows NT y la cláusula catch de C\+\+.  Por consiguiente, llamar explícitamente `_alloca` en escenarios de cualquiera de las siguientes da lugar a errores de programa durante el retorno a la rutina de EH de nomenclatura:  
  
-   Expresión de filtro de excepciones de Windows NT SEH: `__except` \(`_alloca ()` \)  
  
-   Controlador de excepciones final de Windows NT SEH: `__finally` {`_alloca ()` }  
  
-   Expresión de la cláusula catch de C\+\+ EH  
  
 Sin embargo, `_alloca` se puede llamar directamente dentro de una rutina de EH o de una devolución aplicación\- proporcionado obtenga invocado por uno de los escenarios de EH enumeradas anteriormente.  
  
> [!IMPORTANT]
>  En Windows XP, si `_alloca` se denomina dentro de un bloque try\/catch, debe llamar a [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md) en el bloque catch.  
  
 Además de las restricciones anteriores, cuando se utiliza la opción de[\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) , `_alloca` no se puede usar en los bloques de `__except` .  Para obtener más información, vea [\/clr Restricciones](../../build/reference/clr-restrictions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_alloca`|\<malloc.h\>|  
  
## Ejemplo  
  
```  
// crt_alloca.c  
// This program demonstrates the use of  
// _alloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size = 1000;  
    int     errcode = 0;  
    void    *pData = NULL;  
  
    // Note: Do not use try/catch for _alloca,  
    // use __try/__except, since _alloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try {  
        // An unbounded _alloca can easily result in a   
        // stack overflow.  
        // Checking for a size < 1024 bytes is recommended.  
        if (size > 0 && size < 1024)  
        {  
            pData = _alloca( size );  
            printf_s( "Allocated %d bytes of stack at 0x%p",  
                      size, pData);  
        }  
        else  
        {  
            printf_s("Tried to allocate too many bytes.\n");  
        }  
    }  
  
    // If an exception occured with the _alloca function  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_alloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf_s("Could not reset the stack!\n");  
            _exit(1);  
        }  
    };  
}  
```  
  
  **Asignado 1000 bytes de la pila en 0x0012FB50**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)   
 [\_malloca](../../c-runtime-library/reference/malloca.md)