---
title: OUTP, outpw, _outp, _outpw, _outpd
description: Describe las funciones obsoletas y eliminadas OUTP, outpw, _outp, _outpw y _outpd de la biblioteca en tiempo de ejecución de Microsoft C (CRT).
ms.date: 12/09/2019
api_name:
- _outpd
- _outp
- _outpw
- outp
- outpw
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _outpw
- _outpd
- _outp
- outp
- outpw
- outpd
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
ms.openlocfilehash: 03d3df0bae9c2fa3cdd107f3c0de65105077c401
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988376"
---
# <a name="outp-outpw-_outp-_outpw-_outpd"></a>OUTP, outpw, _outp, _outpw, _outpd

Genera, en un puerto, un byte (`outp`, `_outp`), una palabra (`outpw`, `_outpw`) o una palabra doble (`_outpd`).

> [!IMPORTANT]
> Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT.  
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```cpp
int _outp(
   unsigned short port,
   int databyte
);
unsigned short _outpw(
   unsigned short port,
   unsigned short dataword
);
unsigned long _outpd(
   unsigned short port,
   unsigned long dataword
);
```

### <a name="parameters"></a>Parameters

\ de *Puerto*
Número de puerto.

*byte de bits,\ de Word*
Valores de salida.

## <a name="return-value"></a>Valor devuelto

Las funciones devuelven el resultado de datos. No se devuelve ningún error.

## <a name="remarks"></a>Notas

Las funciones `_outp`, `_outpw`y `_outpd` escriben un byte, una palabra y una palabra doble, respectivamente, en el puerto de salida especificado. El argumento de *port* puede ser cualquier entero sin signo del intervalo comprendido entre 0 y 65 535; *databyte* puede ser cualquier entero del intervalo comprendido entre 0 y 255; y *dataword* puede ser cualquier valor del intervalo de un entero, un entero corto sin signo y un entero largo sin signo.

Dado que estas funciones escriben directamente en un puerto de E/S, no se pueden usar en el código de usuario. Para obtener información sobre el uso de puertos de E/S en estos sistemas operativos, busque “Comunicaciones serie en Win32” en MSDN.

Los nombres de `outp` y `outpw` son nombres antiguos y en desuso para las funciones `_outp` y `_outpw`. Para obtener más información, vea [nombres de funciones POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Requisitos de

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[E/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)\
[INP, inpw, _inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)
