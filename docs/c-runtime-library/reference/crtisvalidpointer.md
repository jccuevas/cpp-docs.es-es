---
title: _CrtIsValidPointer
ms.date: 11/04/2016
apiname:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 64197d460cdb7dd26d22196c08151be09df48573
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339330"
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer

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

**_CrtIsValidPointer** devuelve TRUE si el puntero especificado no es null. En las versiones de la biblioteca de CRT anteriores a Visual Studio 2010, devuelve TRUE si el intervalo de memoria es válido para la o las operaciones especificadas. De lo contrario, la función devuelve el FALSE.

## <a name="remarks"></a>Comentarios

A partir de la biblioteca de CRT en Visual Studio 2010, el *tamaño* y *acceso* se omiten los parámetros, y **_CrtIsValidPointer** solo comprueba que el especificado *dirección* no es null. No se recomienda usar esta función porque puede realizar la prueba sin ningún problema. En las versiones anteriores de Visual Studio 2010, la función simplemente comprueba que el intervalo de memoria que empieza en *dirección* y se extiende por *tamaño* bytes es válido para las operaciones de accesibilidad especificadas. Cuando *acceso* está establecida en TRUE, el intervalo de memoria se comprueba para operaciones de lectura y escritura. Cuando *acceso* es FALSE, el intervalo de memoria solo se comprueba para su lectura. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtIsValidPointer** se quitan durante el preprocesamiento.

Dado que esta función devuelve TRUE o FALSE, se puede pasar a una de las macros [_ASSERT](assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si el intervalo de memoria no es válido para operaciones de lectura y escritura:

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Para obtener más información acerca de cómo **_CrtIsValidPointer** puede utilizarse con otras macros y funciones de depuración, vea [Macros para los informes](/visualstudio/debugger/macros-for-reporting). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

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
