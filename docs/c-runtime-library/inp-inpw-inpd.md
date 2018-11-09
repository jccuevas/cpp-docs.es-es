---
title: _inp, _inpw, _inpd
ms.date: 11/04/2016
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: 56587455b1b5246be361afc131786d85dbc9a1a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469867"
---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd

Especifica, desde un puerto, un byte (`_inp`), una palabra (`_inpw`) o una palabra doble (`_inpd`).

> [!IMPORTANT]
>  Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT.

> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

#### <a name="parameters"></a>Parámetros

*puerto*<br/>
Número de puerto de E/S.

## <a name="return-value"></a>Valor devuelto

Las funciones devuelven el byte, la palabra o la palabra doble leída en `port`. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

Las funciones `_inp`, `_inpw`y `_inpd` leen un byte, una palabra y una palabra doble, respectivamente, del puerto de conexión especificado. El valor de entrada puede ser cualquier entero corto sin signo del intervalo comprendido entre 0 y 65 535.

Dado que estas funciones leen directamente desde un puerto de E/S, no se pueden usar en el código de usuario.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[E/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)<br/>
[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)