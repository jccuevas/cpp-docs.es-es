---
title: _CrtIsValidPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 490d2dea097935dee2cd2a003aa28e32f1ced69d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938769"
---
# <a name="_crtisvalidpointer"></a>_CrtIsValidPointer

Comprueba que un puntero no es null. En las versiones de la biblioteca en tiempo de ejecución de C anteriores a Visual Studio 2010, comprueba que un intervalo de memoria especificado es válido para lectura y escritura (solo en la versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtIsValidPointer(
   const void *address,
   unsigned int size,
   int access
);
```

### <a name="parameters"></a>Parámetros

*address*<br/>
Señala al comienzo del intervalo de memoria cuya validez se va a comprobar.

*size*<br/>
Tamaño del intervalo de memoria especificado, en bytes.

*access*<br/>
Accesibilidad de lectura y escritura que se va a determinar para el intervalo de memoria.

## <a name="return-value"></a>Valor devuelto

**_CrtIsValidPointer** devuelve true si el puntero especificado no es NULL. En las versiones de la biblioteca de CRT anteriores a Visual Studio 2010, devuelve TRUE si el intervalo de memoria es válido para la o las operaciones especificadas. De lo contrario, la función devuelve el FALSE.

## <a name="remarks"></a>Comentarios

A partir de la biblioteca de CRT de Visual Studio 2010, se omiten los parámetros de *tamaño* y de *acceso* , y **_CrtIsValidPointer** solo comprueba si la *Dirección* especificada no es NULL. No se recomienda usar esta función porque puede realizar la prueba sin ningún problema. En las versiones anteriores a Visual Studio 2010, la función comprueba que el intervalo de memoria que empieza en la *Dirección* y que se extiende para el *tamaño* de bytes es válido para las operaciones de accesibilidad especificadas. Cuando el *acceso* se establece en true, el intervalo de memoria se comprueba para lectura y escritura. Cuando el *acceso* es false, el intervalo de memoria solo se valida para lectura. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtIsValidPointer** se quitan durante el preprocesamiento.

Dado que esta función devuelve TRUE o FALSE, se puede pasar a una de las macros [_ASSERT](assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si el intervalo de memoria no es válido para operaciones de lectura y escritura:

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Para obtener más información sobre cómo se puede usar **_CrtIsValidPointer** con otras funciones de depuración y macros, vea [macros para informes](/visualstudio/debugger/macros-for-reporting). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_CrtIsValidPointer** es una extensión de Microsoft. Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo del tema [_CrtIsValidHeapPointer](crtisvalidheappointer.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
