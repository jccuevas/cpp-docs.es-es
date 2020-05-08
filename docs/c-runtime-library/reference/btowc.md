---
title: btowc
ms.date: 4/2/2020
api_name:
- btowc
- _o_btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: cbeff70674a257217c66d39475a2c809c9bd9559
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913362"
---
# <a name="btowc"></a>btowc

Determina si un entero representa un carácter de un solo byte válido en el estado de desplazamiento inicial.

## <a name="syntax"></a>Sintaxis

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Parámetros

*óptico*<br/>
Entero que se va a probar.

## <a name="return-value"></a>Valor devuelto

Devuelve la representación de caracteres anchos del carácter si el entero representa un carácter de un solo byte válido en el estado de desplazamiento inicial. Devuelve WEOF si el entero es EOF o no es un carácter de un solo byte válido en el estado de desplazamiento inicial. La salida de esta función se ve afectada por la configuración regional del **LC_TYPE** actual.

## <a name="remarks"></a>Observaciones

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**btowc**|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
