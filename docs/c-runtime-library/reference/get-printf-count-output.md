---
title: _get_printf_count_output
ms.date: 11/04/2016
api_name:
- _get_printf_count_output
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: 15b37ac759821ad56cc5c03c9b98719d8f0cc19a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955710"
---
# <a name="_get_printf_count_output"></a>_get_printf_count_output

Indica si las funciones [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)admiten el formato **% n** .

## <a name="syntax"></a>Sintaxis

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Valor devuelto

Distinto de cero si se admite **% n** , 0 si no se admite **% n** .

## <a name="remarks"></a>Comentarios

Si no se admite **% n** (valor predeterminado), al encontrar **% n** en la cadena de formato de cualquiera de las funciones **printf** , se invocará el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si está habilitada la compatibilidad de **% n** (vea [_set_printf_count_output](set-printf-count-output.md)), **% n** se comportará como se describe en [Sintaxis de especificación de formato: funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_set_printf_count_output](set-printf-count-output.md).

## <a name="see-also"></a>Vea también

[_set_printf_count_output](set-printf-count-output.md)<br/>
