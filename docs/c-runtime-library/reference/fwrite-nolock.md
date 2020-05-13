---
title: _fwrite_nolock
ms.date: 4/2/2020
api_name:
- _fwrite_nolock
- _o__fwrite_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fwrite_nolock
- fwrite_nolock
helpviewer_keywords:
- fwrite_nolock function
- streams, writing data to
- _fwrite_nolock function
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
ms.openlocfilehash: 6856dd2af0536deacfbef6b02c7cdf38d41f9c04
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919430"
---
# <a name="_fwrite_nolock"></a>_fwrite_nolock

Escribe datos en una secuencia sin bloquear el subproceso.

## <a name="syntax"></a>Sintaxis

```C
size_t _fwrite_nolock(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*búfer*<br/>
Puntero a los datos que se van a escribir.

*size*<br/>
Tamaño del elemento en bytes.

*count*<br/>
Número máximo de elementos que se va a escribir.

*misiones*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Igual que [fwrite](fwrite.md).

## <a name="remarks"></a>Observaciones

Esta función es una versión que no es de bloqueo de **fwrite**. Es idéntico a **fwrite** , salvo que no está protegido frente a interferencias de otros subprocesos. Puede ser más rápidas porque no incurre en la sobrecarga de bloquear otros subprocesos. Use esta función solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fwrite_nolock**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fread](fread.md).

## <a name="see-also"></a>Consulta también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fread](fread.md)<br/>
[_write](write.md)<br/>
