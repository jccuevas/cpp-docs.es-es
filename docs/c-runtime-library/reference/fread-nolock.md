---
title: _fread_nolock
ms.date: 11/04/2016
apiname:
- _fread_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fread_nolock
- fread_nolock
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- fread_nolock function
- _fread_nolock function
- streams [C++], reading data from
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
ms.openlocfilehash: 81827363d670c7cdeeddcb86390323bf431c6f98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597293"
---
# <a name="freadnolock"></a>_fread_nolock

Lee datos desde una secuencia, sin bloquear otros subprocesos.

## <a name="syntax"></a>Sintaxis

```C
size_t _fread_nolock(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento de los datos.

*size*<br/>
Tamaño del elemento en bytes.

*count*<br/>
Número máximo de elementos que se va a leer.

*secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Consulte [fread](fread.md).

## <a name="remarks"></a>Comentarios

Esta función es una versión que no sea de bloqueo de **fread**. Es idéntico a **fread** , salvo que no está protegida contra interferencias de otros subprocesos. Puede ser más rápidas porque no incurre en la sobrecarga de bloquear otros subprocesos. Use esta función solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fread_nolock**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
