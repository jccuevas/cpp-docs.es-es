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
ms.openlocfilehash: 48e0e58d2886c5a8bb90a86c81cb785d364666e8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988714"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>INP, _inp, inpw, _inpw, _inpd

Entradas, desde un puerto, un byte (`inp`, `_inp`), una palabra (`inpw`, `_inpw`) o una palabra doble (`_inpd`).

> [!IMPORTANT]
> Estas funciones están obsoletas. A partir de Visual Studio 2015, no están disponibles en CRT.  
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

### <a name="parameters"></a>Parameters

\ de *Puerto*
Número de puerto de E/S.

## <a name="return-value"></a>Valor devuelto

Las funciones devuelven el byte, la palabra o la palabra doble leída en `port`. No se devuelve ningún error.

## <a name="remarks"></a>Notas

Las funciones `_inp`, `_inpw`y `_inpd` leen un byte, una palabra y una palabra doble, respectivamente, del puerto de conexión especificado. El valor de entrada puede ser cualquier entero corto sin signo del intervalo comprendido entre 0 y 65 535.

Dado que estas funciones leen directamente desde un puerto de E/S, no se pueden usar en el código de usuario.

Los nombres de `inp` y `inpw` son nombres antiguos y en desuso para las funciones `_inp` y `_inpw`. Para obtener más información, vea [nombres de funciones POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Requisitos de

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[E/S de consola y de puerto](../c-runtime-library/console-and-port-i-o.md)\
[OUTP, outpw, _outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
