---
title: _msize
ms.date: 4/2/2020
api_name:
- _msize
- _o__msize
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- msize
- _msize
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
ms.openlocfilehash: cc8eef0d28f649340715edbf4b1ebdfea85c2ff2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914611"
---
# <a name="_msize"></a>_msize

Devuelve el tamaño de un bloque de memoria asignado en el montón.

## <a name="syntax"></a>Sintaxis

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria.

## <a name="return-value"></a>Valor devuelto

**_msize** devuelve el tamaño (en bytes) como un entero sin signo.

## <a name="remarks"></a>Observaciones

La función **_msize** devuelve el tamaño, en bytes, del bloque de memoria asignado por una llamada a **calloc**, **malloc**o **realloc**.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **_msize** se resuelve en [_msize_dbg](msize-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

Esta función valida su parámetro. Si *memblock* es un puntero nulo, **_msize** invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se controla el error, la función establece **errno** en **EINVAL** y devuelve-1.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [realloc](realloc.md).

## <a name="see-also"></a>Consulta también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
