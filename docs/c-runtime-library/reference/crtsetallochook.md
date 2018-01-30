---
title: _CrtSetAllocHook | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6168081aff668a3b613b4844be3c50b841f5bc07
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook
Instala una función de asignación definida por el cliente enlazándola al proceso de asignación de memoria de depuración en tiempo de ejecución de C (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_CRT_ALLOC_HOOK _CrtSetAllocHook(  
   _CRT_ALLOC_HOOK allocHook   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `allocHook`  
 Nueva función de asignación definida por el cliente que se va a enlazar al proceso de asignación de memoria de depuración en tiempo de ejecución de C.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve la función de enlace de asignación previamente definida, o `NULL` si `allocHook` es `NULL`.  
  
## <a name="remarks"></a>Comentarios  
 `_CrtSetAllocHook` permite que una aplicación enlace su propia función de asignación al proceso de asignación de memoria de la biblioteca de depuración en tiempo de ejecución de C. Como resultado, todas las llamadas a una función de asignación de depuración para asignar, reasignar o liberar un bloque de memoria desencadena una llamada a la función de enlace de la aplicación. `_CrtSetAllocHook` proporciona a una aplicación un método sencillo para probar cómo controla la aplicación las situaciones de memoria insuficiente, la capacidad de examinar patrones de asignación y la posibilidad de registrar información de asignación para un análisis posterior. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtSetAllocHook` se quitan durante el preprocesamiento.  
  
 La función `_CrtSetAllocHook` instala la nueva función de asignación definida por el cliente especificada en `allocHook` y devuelve la función de enlace definida previamente. En el ejemplo siguiente se muestra cómo se deben crear prototipos de un enlace de asignación definido por el cliente:  
  
```  
int YourAllocHook( int allocType, void *userData, size_t size, int   
blockType, long requestNumber, const unsigned char *filename, int   
lineNumber);  
```  
  
 El argumento de `allocType` especifica el tipo de operación de asignación `(_HOOK_ALLOC`, `_HOOK_REALLOC` y `_HOOK_FREE`) que desencadenó la llamada a la función de enlace de asignación. Cuando el tipo de asignación desencadenante es `_HOOK_FREE`, `userData` es un puntero a la sección de datos de usuario del bloque de memoria que se va a liberar. Sin embargo, cuando el tipo de asignación desencadenante es `_HOOK_ALLOC` o `_HOOK_REALLOC`, `userData` es `NULL`, porque el bloque de memoria no se ha asignado todavía.  
  
 `size` especifica el tamaño del bloque de memoria en bytes, `blockType` indica el tipo de bloque de memoria, `requestNumber` es el número de orden de asignación de objetos del bloque de memoria, y, si están disponibles, `filename` y `lineNumber` especifican el nombre del archivo y el número de línea donde se inició la operación de asignación desencadenante.  
  
 Una vez que la función de enlace se ha terminado de procesar, debe devolver un valor booleano, que indica al proceso de asignación principal en tiempo de ejecución de C cómo continuar. Si la función de enlace indica que el proceso de asignación principal debe continuar como si no se hubiera llamado a la función de enlace, la función de enlace debe devolver `TRUE`. De esta forma, se ejecuta la operación de asignación desencadenante original. Con esta implementación, la función de enlace puede recopilar y guardar información de asignación para un análisis posterior, sin interferir con la operación de asignación actual ni el estado del montón de depuración.  
  
 Si la función de enlace indica que el proceso de asignación principal debe continuar como si se hubiera producido un error al llamar a la función de asignación desencadenante, la función de enlace debe devolver `FALSE`. Con esta implementación, la función de enlace puede simular gran cantidad de condiciones de memoria y estados de montón de depuración para comprobar cómo controla la aplicación las distintas situaciones.  
  
 Para borrar la función de enlace, pase `NULL` a `_CrtSetAllocHook`.  
  
 Para obtener más información sobre cómo se puede usar `_CrtSetAllocHook` con otras funciones de administración de memoria o cómo escribir funciones de enlace definidas por el cliente, consulte [Creación de funciones de enlace de depuración](/visualstudio/debugger/debug-hook-function-writing).  
  
> [!NOTE]
>  `_CrtSetAllocHook` no es compatible con `/clr:pure`. Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtSetAllocHook`|\<crtdbg.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtSetAllocHook`, consulte [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_CrtGetAllocHook](../../c-runtime-library/reference/crtgetallochook.md)