---
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: 303f682b54abc5e44cb7fdd4c89012dd9913288b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938484"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

Instala una función de asignación definida por el cliente enlazándola al proceso de asignación de memoria de depuración en tiempo de ejecución de C (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>Parámetros

*allocHook*<br/>
Nueva función de asignación definida por el cliente que se va a enlazar al proceso de asignación de memoria de depuración en tiempo de ejecución de C.

## <a name="return-value"></a>Valor devuelto

Devuelve la función de enlace de asignación definida previamente, o **null** si *allocHook* es **null**.

## <a name="remarks"></a>Comentarios

**_CrtSetAllocHook** permite que una aplicación enlace su propia función de asignación al proceso de asignación de memoria de la biblioteca de depuración en tiempo de ejecución de C. Como resultado, todas las llamadas a una función de asignación de depuración para asignar, reasignar o liberar un bloque de memoria desencadena una llamada a la función de enlace de la aplicación. **_CrtSetAllocHook** proporciona a una aplicación un método sencillo para probar cómo controla la aplicación las situaciones de memoria insuficiente, la capacidad de examinar patrones de asignación y la posibilidad de registrar información de asignación para un análisis posterior. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtSetAllocHook** se quitan durante el preprocesamiento.

La función **_CrtSetAllocHook** instala la nueva función de asignación definida por el cliente especificada en *allocHook* y devuelve la función de enlace definida previamente. En el ejemplo siguiente se muestra cómo se deben crear prototipos de un enlace de asignación definido por el cliente:

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

El argumento **allocType** especifica el tipo de operación de asignación ( **_HOOK_ALLOC**, **_HOOK_REALLOC**y **_HOOK_FREE**) que desencadenó la llamada a la función de enlace de la asignación. Cuando el tipo de asignación desencadenante es **_HOOK_FREE**, *UserData* es un puntero a la sección de datos de usuario del bloque de memoria que se va a liberar. Sin embargo, cuando el tipo de asignación desencadenante es **_HOOK_ALLOC** o **_HOOK_REALLOC**, *UserData* es **null** porque todavía no se ha asignado el bloque de memoria.

*size* especifica el tamaño del bloque de memoria en bytes, *blockType* indica el tipo del bloque de memoria, *requestNumber* es el número de orden de asignación de objetos del bloque de memoria y, si está disponible, *filename* y **lineNumber** especifique el nombre del archivo de código fuente y el número de línea donde se inició la operación de asignación desencadenante.

Una vez que la función de enlace se ha terminado de procesar, debe devolver un valor booleano, que indica al proceso de asignación principal en tiempo de ejecución de C cómo continuar. Cuando la función de enlace desea que el proceso de asignación principal continúe como si nunca se hubiera llamado a la función de enlace, la función de enlace debe devolver **true**. De esta forma, se ejecuta la operación de asignación desencadenante original. Con esta implementación, la función de enlace puede recopilar y guardar información de asignación para un análisis posterior, sin interferir con la operación de asignación actual ni el estado del montón de depuración.

Cuando la función de enlace desea que el proceso de asignación principal continúe como si se llamara a la operación de asignación desencadenante y se produjo un error, la función de enlace debe devolver el **valor false**. Con esta implementación, la función de enlace puede simular gran cantidad de condiciones de memoria y estados de montón de depuración para comprobar cómo controla la aplicación las distintas situaciones.

Para borrar la función de enlace, pase **null** a **_CrtSetAllocHook**.

Para obtener más información sobre cómo se puede usar **_CrtSetAllocHook** con otras funciones de administración de memoria o cómo escribir sus propias funciones de enlace definidas por el cliente, consulte escritura de funciones de [enlace de depuración](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** no se admite en **/clr: Pure**. Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y se han quitado en Visual Studio 2017.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_CrtSetAllocHook**, consulte [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
