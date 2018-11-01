---
title: _get_printf_count_output
ms.date: 11/04/2016
apiname:
- _get_printf_count_output
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
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: 477e4a9e987f27bd70b9707e91b9ea9d84b69993
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610644"
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

Indica si [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-familia de funciones de compatibilidad con la **%n** formato.

## <a name="syntax"></a>Sintaxis

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Valor devuelto

Distinto de cero si **%n** es compatible, 0 si **%n** no se admite.

## <a name="remarks"></a>Comentarios

Si **%n** es no admite (valor predeterminado), produciendo **%n** en la cadena de formato de cualquiera de los **printf** funciones invocará el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si **%n** compatibilidad está habilitada (vea [_set_printf_count_output](set-printf-count-output.md)), a continuación, **%n** se comportará tal como se describe en [sintaxis de especificación de formato: printf y wprintf Funciones](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_set_printf_count_output](set-printf-count-output.md).

## <a name="see-also"></a>Vea también

[_set_printf_count_output](set-printf-count-output.md)<br/>
