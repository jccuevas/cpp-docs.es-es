---
title: "_CrtIsValidHeapPointer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtIsValidHeapPointer"
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
  - "CrtlsValidHeapPointer"
  - "_CrtIsValidHeapPointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtIsValidHeapPointer (función)"
  - "CrtIsValidHeapPointer (función)"
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _CrtIsValidHeapPointer
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comprueba si un puntero especificado se encuentra en un montón asignado por alguna biblioteca en tiempo de ejecución de C, pero no necesariamente por la biblioteca CRT del autor de llamada.  En las versiones de CRT anteriores a Visual Studio 2010, comprueba que el puntero especificado se encuentre en el montón local \(solo en la versión de depuración\).  
  
## Sintaxis  
  
```  
  
        int _CrtIsValidHeapPointer(   
   const void *userData   
);  
```  
  
#### Parámetros  
 `userData`  
 Puntero al principio de un bloque de memoria asignado.  
  
## Valor devuelto  
 `_CrtIsValidHeapPointer` devuelve TRUE si el puntero especificado se encuentra en el montón que comparten todas las instancias de la biblioteca CRT.  En las versiones de CRT anteriores a Visual Studio 2010, devuelve TRUE si el puntero especificado se encuentra en el montón local.  De lo contrario, la función devuelve el FALSE.  
  
## Comentarios  
 No se recomienda usar esta función.  A partir de la biblioteca CRT de Visual Studio 2010, todas las bibliotecas CRT comparten un montón de SO, el *montón de procesos*.  La función `_CrtIsValidHeapPointer` indica si el puntero se asignó en un montón CRT, pero no si lo asignó la biblioteca CRT del autor de la llamada.  Por ejemplo, tenga en cuenta un bloque asignado mediante la versión de Visual Studio 2010 de la biblioteca CRT.  Si la función `_CrtIsValidHeapPointer` exportada por la versión de Visual Studio 2012 de la biblioteca CRT comprueba el puntero, devuelve TRUE.  Esta prueba ya no es útil.  En versiones anteriores a Visual Studio 2010 de la biblioteca CRT, la función se usa para garantizar que una dirección de memoria concreta está en el montón local.  El montón local hace referencia al montón creado y administrado por una instancia determinada de la biblioteca en tiempo de ejecución de C.  Si una biblioteca de vínculos dinámicos \(DLL\) contiene un vínculo estático a la biblioteca en tiempo de ejecución, tiene su propia instancia del montón en tiempo de ejecución y, por consiguiente, su propio montón, independiente del montón local de la aplicación.  Cuando no se define [\_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtIsValidHeapPointer` se quitan durante el preprocesamiento.  
  
 Dado que esta función devuelve TRUE o FALSE, se puede pasar a una de las macros de [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración.  En el ejemplo siguiente se genera un error de aserción si la dirección especificada no se está en el montón local:  
  
```  
_ASSERTE( _CrtIsValidHeapPointer( userData ) );  
```  
  
 Para obtener más información sobre cómo usar `_CrtIsValidHeapPointer` con otras macros y funciones de depuración, vea [Macros para los informes](../Topic/Macros%20for%20Reporting.md).  Para obtener más información sobre cómo asignar, inicializar y administrar los bloques de memoria en la versión de depuración del montón base, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_CrtIsValidHeapPointer`|\<crtdbg.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Solo las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo probar si la memoria es válida cuando se utiliza con las bibliotecas de tiempo de ejecución de C anteriores a Visual Studio 2010.  Este ejemplo se proporciona para los usuarios de código heredado de la biblioteca CRT.  
  
```  
// crt_isvalid.c  
/*  
 * This program allocates a block of memory using _malloc_dbg  
 * and then tests the validity of this memory by calling   
 * _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
#define  TRUE   1  
#define  FALSE  0  
  
int main( void )  
{  
        char *my_pointer;  
  
        /*   
         * Call _malloc_dbg to include the filename and line number  
         * of our allocation request in the header information  
         */  
        my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,   
        _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
        // Ensure that the memory got allocated correctly  
        _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,   
        NULL, NULL, NULL );  
  
         // Test for read/write accessibility  
        if (_CrtIsValidPointer((const void *)my_pointer,   
        sizeof(char) * 10, TRUE))  
                printf("my_pointer has read and write accessibility.\n");  
        else  
                printf("my_pointer only has read access.\n");  
  
        // Make sure my_pointer is within the local heap  
        if (_CrtIsValidHeapPointer((const void *)my_pointer))  
                printf("my_pointer is within the local heap.\n");  
        else  
                printf("my_pointer is not located within the local"  
                       " heap.\n");  
  
        free(my_pointer);  
}  
```  
  
## Salida  
  
```  
my_pointer has read and write accessibility.  
my_pointer is within the local heap.  
```  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)