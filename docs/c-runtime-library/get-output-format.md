---
title: _get_output_format
ms.date: 11/04/2016
api_name:
- _get_output_format
api_location:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_output_format
- _get_output_format
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
ms.openlocfilehash: 682ab9796942e52ed036193887158ea22b738189
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349334"
---
# <a name="_get_output_format"></a>_get_output_format

Obtiene el valor actual de la marca del formato de salida.

> [!IMPORTANT]
> Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.

## <a name="syntax"></a>Sintaxis

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>Valor devuelto

El valor actual de la marca del formato de salida.

## <a name="remarks"></a>Observaciones

La marca del formato de salida controla las características de la E/S con formato. En la actualidad, la marca tiene dos valores posibles: 0 y `_TWO_DIGIT_EXPONENT`. Si se establece `_TWO_DIGIT_EXPONENT` , los números de punto flotante se imprimen solo con dos dígitos en el exponente, a menos el tamaño del exponente requiera un tercer dígito. Si la marca es cero, la salida de punto flotante muestra tres dígitos del exponente, con ceros si es necesario para rellenar el valor hasta los tres dígitos.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../c-runtime-library/compatibility.md) en la introducción.

## <a name="see-also"></a>Consulte también

[Sintaxis de especificación de formato: funciones printf y wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)
