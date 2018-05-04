---
title: _CrtSetAllocHook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d86072ceb41b966adfca298152b6209450aace3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook

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

Devuelve la función de enlace de asignación previamente definida, o **NULL** si *allocHook* es **NULL**.

## <a name="remarks"></a>Comentarios

**_CrtSetAllocHook** permite que una aplicación enlace su propia función de asignación en el proceso de asignación de memoria de biblioteca de C depuración en tiempo de ejecución. Como resultado, todas las llamadas a una función de asignación de depuración para asignar, reasignar o liberar un bloque de memoria desencadena una llamada a la función de enlace de la aplicación. **_CrtSetAllocHook** proporciona una aplicación con un método sencillo para probar cómo controla la aplicación las situaciones de memoria insuficiente, la capacidad para examinar pautas de asignación y la posibilidad de registrar información de asignación para más tarde análisis. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtSetAllocHook** se quitan durante el preprocesamiento.

El **_CrtSetAllocHook** función instala la nueva función de asignación definida por el cliente especificada en *allocHook* y devuelve la función de enlace definida previamente. En el ejemplo siguiente se muestra cómo se deben crear prototipos de un enlace de asignación definido por el cliente:

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

El **allocType** argumento especifica el tipo de operación de asignación (**_HOOK_ALLOC**, **_HOOK_REALLOC**, y **_HOOK_FREE**) que desencadena la llamada a función de enlace de asignación. Cuando el tipo de asignación desencadenante es **_HOOK_FREE**, *userData* es un puntero a la sección de datos de usuario del bloque de memoria que se va a liberar. Sin embargo, cuando el tipo de asignación desencadenante es **_HOOK_ALLOC** o **_HOOK_REALLOC**, *userData* es **NULL** porque bloquear la memoria no se ha asignado todavía.

*tamaño* especifica el tamaño de la memoria de bloque en bytes, *existen* indica el tipo del bloque de memoria, *requestNumber* es el número de orden de asignación de objetos del bloque de memoria y, disponible, *filename* y **lineNumber** especificar el origen archivo nombre y número de línea donde se inició la operación de asignación desencadenante.

Una vez que la función de enlace se ha terminado de procesar, debe devolver un valor booleano, que indica al proceso de asignación principal en tiempo de ejecución de C cómo continuar. Cuando la función de enlace indica que el proceso de asignación principal debe continuar como si nunca se hubiera llamado la función de enlace, la función de enlace debe devolver **TRUE**. De esta forma, se ejecuta la operación de asignación desencadenante original. Con esta implementación, la función de enlace puede recopilar y guardar información de asignación para un análisis posterior, sin interferir con la operación de asignación actual ni el estado del montón de depuración.

Cuando la función de enlace indica que el proceso de asignación principal debe continuar como si se llamó a la operación de asignación desencadenante y se produjo un error, a continuación, la función de enlace debe devolver **FALSE**. Con esta implementación, la función de enlace puede simular gran cantidad de condiciones de memoria y estados de montón de depuración para comprobar cómo controla la aplicación las distintas situaciones.

Para borrar la función de enlace, pasar **NULL** a **_CrtSetAllocHook**.

Para obtener más información acerca de cómo **_CrtSetAllocHook** puede utilizarse con otras funciones de administración de memoria o cómo escribir sus propias funciones de enlace definida por el cliente, consulte [creación de funciones de enlace de depuración](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** no es compatible con **/CLR: pure**. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y se quitó en Visual Studio de 2017.

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
