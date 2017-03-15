---
title: _malloca | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _malloca
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- malloca
- _malloca
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 70a37640ec7f6024539ad1e2134152190e698133
ms.lasthandoff: 02/24/2017

---
# <a name="malloca"></a>_malloca
Asigna memoria en la pila. Se trata de una versión de [_alloca](../../c-runtime-library/reference/alloca.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *_malloca(   
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `size`  
 Bytes que se van a asignar desde la pila.  
  
## <a name="return-value"></a>Valor devuelto  
 La rutina `_malloca` devuelve un puntero `void` al espacio asignado, cuya correcta alineación para almacenar cualquier tipo de objeto está garantizada. Si `size` es 0, `_malloca` asigna un elemento de longitud cero y devuelve un puntero válido para ese elemento.  
  
 Si no se puede asignar el espacio, se genera una excepción de desbordamiento de pila. La excepción de desbordamiento de pila no es una excepción de C++, sino que es una excepción estructurada. En lugar de usar el control de excepciones de C++, debe usar el [control de excepciones estructuradas](../../cpp/structured-exception-handling-c-cpp.md) (SEH).  
  
## <a name="remarks"></a>Comentarios  
 `_malloca` asigna `size` bytes de la pila del programa o del montón si la solicitud supera un determinado tamaño en bytes proporcionado por `_ALLOCA_S_THRESHOLD`. La diferencia entre `_malloca` y `_alloca` es que `_alloca` siempre se asigna en la pila, independientemente del tamaño. A diferencia de `_alloca`, que no requiere ni permite ninguna llamada a `free` para liberar la memoria asignada, `_malloca` requiere el uso de [_freea](../../c-runtime-library/reference/freea.md) para liberar memoria. En el modo de depuración, `_malloca` siempre asigna memoria del montón.  
  
 Existen restricciones para llamar explícitamente a `_malloca` en un controlador de excepciones. Las rutinas del controlador de excepciones que se ejecutan en procesadores de clase x86 funcionan en su propio marco de memoria: llevan a cabo sus tareas en el espacio de memoria que no se basa en la ubicación actual del puntero de pila de la función de inclusión. Las implementaciones más habituales incluyen el control de excepciones estructuradas (SEH) de Windows NT y las expresiones de la cláusula catch de C++. Por consiguiente, si se llama explícitamente a `_malloca` en cualquiera de los siguientes escenarios, se produce un error del programa durante la devolución de la rutina del controlador de excepciones a la que se llama:  
  
-   Expresión de filtro de excepciones SEH de Windows NT: `__except` (`_malloca ()`)  
  
-   Controlador de excepciones finales SEH de Windows NT: `__finally` {`_malloca ()`}  
  
-   Expresión de la cláusula catch del controlador de excepciones de C++  
  
 Sin embargo, se puede llamar directamente a `_malloca` desde dentro de una rutina del controlador de excepciones o desde una devolución de llamada proporcionada por la aplicación, invocada mediante uno de los escenarios del controlador de excepciones que se han descrito anteriormente.  
  
> [!IMPORTANT]
>  En Windows XP, si se llama a `_malloca` dentro de un bloque try/catch, debe llamar a [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md) en el bloque catch.  
  
 Además de las restricciones anteriores, si se usa la opción [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), no se puede usar `_malloca` en los bloques `__except`. Para obtener más información, vea [Restricciones de /clr](../../build/reference/clr-restrictions.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_malloca`|\<malloc.h>|  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="input"></a>Entrada  
  
```  
1000  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
Enter the number of bytes to allocate using _malloca: 1000  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)
