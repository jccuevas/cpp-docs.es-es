---
title: _alloca | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _alloca
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
- _alloca
- alloca
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, stack
- alloca function
- _alloca function
ms.assetid: 74488eb1-b71f-4515-88e1-cdd03b6f8225
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 5875a26dc5758674665fba2fde5b51c2ff53420e
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="alloca"></a>_alloca
Asigna memoria en la pila. Esta función está desusada porque hay una versión más segura; vea [_malloca](../../c-runtime-library/reference/malloca.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *_alloca(   
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `size`  
 Bytes que se van a asignar desde la pila.  
  
## <a name="return-value"></a>Valor devuelto  
 La rutina `_alloca` devuelve un puntero `void` al espacio asignado, cuya correcta alineación para almacenar cualquier tipo de objeto está garantizada. Si `size` es 0, `_alloca` asigna un elemento de longitud cero y devuelve un puntero válido para ese elemento.  
  
 Si no se puede asignar el espacio, se genera una excepción de desbordamiento de pila. La excepción de desbordamiento de pila no es una excepción de C++, sino que es una excepción estructurada. En lugar de usar el control de excepciones de C++, debe usar el [control de excepciones estructuradas](../../cpp/structured-exception-handling-c-cpp.md) (SEH).  
  
## <a name="remarks"></a>Comentarios  
 `_alloca`asigna `size` bytes a partir de la pila del programa. El espacio asignado se libera automáticamente cuando finaliza la función que realiza la llamada (no cuando la asignación simplemente queda fuera del ámbito). Por lo tanto, no pase el valor de puntero devuelto por `_alloca` como argumento a [libre](../../c-runtime-library/reference/free.md).  
  
 Existen restricciones para llamar explícitamente a `_alloca` en un controlador de excepciones. Las rutinas del controlador de excepciones que se ejecutan en procesadores de clase x86 funcionan en su propio marco de memoria: llevan a cabo sus tareas en el espacio de memoria que no se basa en la ubicación actual del puntero de pila de la función de inclusión. Las implementaciones más habituales incluyen el control de excepciones estructuradas (SEH) de Windows NT y las expresiones de la cláusula catch de C++. Por consiguiente, si se llama explícitamente a `_alloca` en cualquiera de los siguientes escenarios, se produce un error del programa durante la devolución de la rutina del controlador de excepciones a la que se llama:  
  
-   Expresión de filtro de excepciones SEH de Windows NT: `__except` (`_alloca ()`)  
  
-   Controlador de excepciones finales SEH de Windows NT: `__finally` {`_alloca ()`}  
  
-   Expresión de la cláusula catch del controlador de excepciones de C++  
  
 Sin embargo, se puede llamar directamente a `_alloca` desde dentro de una rutina del controlador de excepciones o desde una devolución de llamada proporcionada por la aplicación, invocada mediante uno de los escenarios del controlador de excepciones que se han descrito anteriormente.  
  
> [!IMPORTANT]
>  En Windows XP, si se llama a `_alloca` dentro de un bloque try/catch, debe llamar a [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md) en el bloque catch.  
  
 Además de las restricciones anteriores, cuando se usa el[/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) opción, `_alloca` no se puede usar en `__except` bloques. Para obtener más información, consulta [/clr Restrictions](../../build/reference/clr-restrictions.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_alloca`|\<malloc.h>|  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
Allocated 1000 bytes of stack at 0x0012FB50  
```  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_resetstkoflw](../../c-runtime-library/reference/resetstkoflw.md)   
 [_malloca](../../c-runtime-library/reference/malloca.md)
