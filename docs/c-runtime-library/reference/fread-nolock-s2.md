---
title: _fread_nolock_s2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
dev_langs:
- C++
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db0cd82d251595be586b46fb66a0f0262484e2f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="freadnolocks"></a>_fread_nolock_s

Lee datos desde una secuencia, sin bloquear otros subprocesos. Esta versión de [fread_nolock](fread-nolock.md) incluye mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
size_t _fread_nolock_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t elementCount,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Ubicación de almacenamiento de los datos.

*BufferSize*<br/>
Tamaño del búfer de destino en bytes.

*elementSize*<br/>
Tamaño del elemento que se va a leer en bytes.

*valor de elementCount*<br/>
Número máximo de elementos que se va a leer.

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Consulte [fread_s](fread-s.md).

## <a name="remarks"></a>Comentarios

Esta función es una versión no realiza el bloqueo de **fread_s**. Es idéntico a **fread_s** salvo que no está protegida contra interferencias de otros subprocesos. Puede ser más rápidas porque no incurre en la sobrecarga de bloquear otros subprocesos. Use esta función solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fread_nolock_s**|C: \<stdio.h>; C++: \<cstdio> o \<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
