---
title: _outp, _outpw, _outpd
ms.date: 11/04/2016
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _outpw
- _outpd
- _outp
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
ms.openlocfilehash: 1a507f4115a48372706590eb61f9e3e77a0e3548
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752069"
---
# <a name="outp-outpw-outpd"></a>_outp, _outpw, _outpd

Genera, en un puerto, un byte (`_outp`), una palabra (`_outpw`) o a una palabra doble (`_outpd`).

> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT.

> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```

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

#### <a name="parameters"></a>Parámetros
*port*<br/>
Número de puerto.

*databyte, dataword*<br/>
Valores de salida.

## <a name="return-value"></a>Valor devuelto

Las funciones devuelven el resultado de datos. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

Las funciones `_outp`, `_outpw`y `_outpd` escriben un byte, una palabra y una palabra doble, respectivamente, en el puerto de salida especificado. El argumento de *port* puede ser cualquier entero sin signo del intervalo comprendido entre 0 y 65 535; *databyte* puede ser cualquier entero del intervalo comprendido entre 0 y 255; y *dataword* puede ser cualquier valor del intervalo de un entero, un entero corto sin signo y un entero largo sin signo.

Dado que estas funciones escriben directamente en un puerto de E/S, no se pueden usar en el código de usuario. Para obtener información sobre el uso de puertos de E/S en estos sistemas operativos, busque “Comunicaciones serie en Win32” en MSDN.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[E/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)<br/>
[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)
