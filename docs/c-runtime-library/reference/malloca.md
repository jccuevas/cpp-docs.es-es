---
title: "_malloca | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_malloca"
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
  - "malloca"
  - "_malloca"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_malloca (función)"
  - "malloca (función)"
  - "asignación de memoria, pila"
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _malloca
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna memoria en la pila.  Ésta es una versión de [\_alloca](../../c-runtime-library/reference/alloca.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
void *_malloca(   
   size_t size   
);  
```  
  
#### Parámetros  
 `size`  
 Bytes que se afectarán asignado de la pila.  
  
## Valor devuelto  
 La rutina de `_malloca` devuelve un puntero de `void` el espacio asignado, que se garantiza alinearse convenientemente para el almacenamiento de cualquier tipo de objeto.  Si `size` es 0, `_malloca` asigna un elemento de la cero\- longitud y devuelve un puntero válido a ese elemento.  
  
 Se genera una excepción de desbordamiento de pila si el espacio no puede estar asignado.  La excepción de desbordamiento de pila no es excepción de c\+\+.; es una excepción estructurada.  En lugar de utilizar el control de excepciones de C\+\+, debe utilizar [Control de excepciones estructurado](../../cpp/structured-exception-handling-c-cpp.md) \(SEH\).  
  
## Comentarios  
 `_malloca` asigna los bytes de `size` de la pila del programa o de la pila si la solicitud supera un tamaño en los bytes especificados por `_ALLOCA_S_THRESHOLD`.  La diferencia entre `_malloca` y `_alloca` es que `_alloca` asigna siempre en la pila, independientemente del tamaño.  A diferencia de `_alloca`, que no requiere ni permite que una llamada a `free` libere la memoria asignada en, `_malloca` requiere el uso de [\_freea](../../c-runtime-library/reference/freea.md) para liberar memoria.  En modo de depuración, `_malloca` asigna siempre memoria de montón.  
  
 Hay restricciones explícitamente a `_malloca` en un controlador de excepciones \(EH\).  Las rutinas de EH que se ejecutan en procesadores de x86\-class funcionan en su propio cuadro de memoria: Realizan las tareas en el espacio de memoria que no se basa en la ubicación actual del puntero de pila de la función envolvente.  Las implementaciones más comunes incluyen expresiones de control estructurado de excepciones \(SEH\) de windows NT y la cláusula catch de C\+\+.  Por consiguiente, llamar explícitamente `_malloca` en escenarios de cualquiera de las siguientes da lugar a errores de programa durante el retorno a la rutina de EH de nomenclatura:  
  
-   Expresión de filtro de excepciones de Windows NT SEH: `__except` \(`_malloca ()` \)  
  
-   Controlador de excepciones final de Windows NT SEH: `__finally` {`_malloca ()` }  
  
-   Expresión de la cláusula catch de C\+\+ EH  
  
 Sin embargo, `_malloca` se puede llamar directamente dentro de una rutina de EH o de una devolución aplicación\- proporcionado obtenga invocado por uno de los escenarios de EH enumeradas anteriormente.  
  
> [!IMPORTANT]
>  En Windows XP, si `_malloca` se denomina dentro de un bloque try\/catch, debe llamar a [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md) en el bloque catch.  
  
 Además de las restricciones anteriores, cuando se utiliza la opción de [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) , `_malloca` no se puede usar en los bloques de `__except` .  Para obtener más información, vea [\/clr Restricciones](../../build/reference/clr-restrictions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_malloca`|\<malloc.h\>|  
  
## Ejemplo  
  
```  
// crt_malloca_simple.c  
#include <stdio.h>  
#include <malloc.h>  
  
void Fn()  
{  
   char * buf = (char *)_malloca( 100 );  
   // do something with buf  
   _freea( buf );  
}  
  
int main()  
{  
   Fn();  
}  
```  
  
## Ejemplo  
  
```  
// crt_malloca_exception.c  
// This program demonstrates the use of  
// _malloca and trapping any exceptions  
// that may occur.  
  
#include <windows.h>  
#include <stdio.h>  
#include <malloc.h>  
  
int main()  
{  
    int     size;  
    int     numberRead = 0;  
    int     errcode = 0;  
    void    *p = NULL;  
    void    *pMarker = NULL;  
  
    while (numberRead == 0)  
    {  
        printf_s("Enter the number of bytes to allocate "  
                 "using _malloca: ");  
        numberRead = scanf_s("%d", &size);  
    }  
  
    // Do not use try/catch for _malloca,  
    // use __try/__except, since _malloca throws  
    // Structured Exceptions, not C++ exceptions.  
  
    __try  
    {  
        if (size > 0)  
        {  
            p =  _malloca( size );  
        }  
        else  
        {  
            printf_s("Size must be a positive number.");  
        }  
        _freea( p );  
    }  
  
    // Catch any exceptions that may occur.  
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )  
    {  
        printf_s("_malloca failed!\n");  
  
        // If the stack overflows, use this function to restore.  
        errcode = _resetstkoflw();  
        if (errcode)  
        {  
            printf("Could not reset the stack!");  
            _exit(1);  
        }  
    };  
}  
```  
  
## Entrada  
  
```  
1000  
```  
  
## Resultados del ejemplo  
  
```  
Enter the number of bytes to allocate using _malloca: 1000  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)