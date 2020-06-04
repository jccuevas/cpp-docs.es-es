---
title: INP, _inp, inpw, _inpw, _inpd
description: Describe las funciones de la biblioteca de tiempo de ejecución de Microsoft C (CRT) que están obsoletas y se han _inpd _inpw _inp quitado.
ms.date: 12/09/2019
api_name:
- inp
- inpw
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inp
- inpw
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
ms.openlocfilehash: f7b822c4b694969407e32ba26026465fb39bd8d6
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825834"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>INP, _inp, inpw, _inpw, _inpd

Entradas, desde un puerto, un byte (`inp`, `_inp`), una palabra (`inpw`, `_inpw`) o una palabra doble (`_inpd`).

> [!IMPORTANT]
> Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT. \
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```cpp
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

### <a name="parameters"></a>Parámetros

*casilla*\
Número de puerto de E/S.

## <a name="return-value"></a>Valor devuelto

Las funciones devuelven el byte, la palabra o la palabra doble leída en `port`. No se devuelve ningún error.

## <a name="remarks"></a>Observaciones

Las funciones `_inp`, `_inpw`y `_inpd` leen un byte, una palabra y una palabra doble, respectivamente, del puerto de conexión especificado. El valor de entrada puede ser cualquier entero corto sin signo del intervalo comprendido entre 0 y 65 535.

Dado que estas funciones leen directamente desde un puerto de E/S, no se pueden usar en el código de usuario.

Los `inp` nombres `inpw` y son nombres más antiguos y desusados `_inp` para `_inpw` las funciones y. Para obtener más información, vea [nombres de funciones POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulte también

[E/s de consola y Puerto](../c-runtime-library/console-and-port-i-o.md)\
[OUTP, outpw, _outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
