---
title: _gcvt_s | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _gcvt_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _gcvt_s
- gcvt_s
dev_langs:
- C++
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60f68507f25ba6255b1c6a439c5e74729d2a2646
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="gcvts"></a>_gcvt_s

Convierte un valor de punto flotante en una cadena. Se trata de una versión de [_gcvt](gcvt.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Búfer en que se va a almacenar el resultado de la conversión.

*sizeInBytes*<br/>
Tamaño del búfer.

*valor*<br/>
Valor que se va a convertir.

*digits*<br/>
Número de dígitos significativos almacenados.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si se produce un error debido a un parámetro no válido (vea la tabla siguiente para consultar valores no válidos), se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, se devuelve un código de error. Los códigos de error se definen en Errno.h. Para obtener una lista de estos errores, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Condiciones de error

|*buffer*|*sizeInBytes*|*valor*|*digits*|Volver|Valor de *búfer*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|any|any|any|**EINVAL**|No modificado.|
|No **NULL** (apunta a la memoria válido)|cero|any|any|**EINVAL**|No modificado.|
|No **NULL** (apunta a la memoria válido)|any|any|>= *sizeInBytes*|**EINVAL**|No modificado.|

**Problemas de seguridad**

**_gcvt_s** puede generar una infracción de acceso si *búfer* no apunta a la memoria válido y no es **NULL**.

## <a name="remarks"></a>Comentarios

El **_gcvt_s** función convierte un punto flotante *valor* en una cadena de caracteres (que incluye un separador decimal y un byte de inicio de sesión posible) y almacena la cadena de *búfer* . *búfer* debe ser lo suficientemente grande como para alojar el valor convertido más de un carácter null final, que se anexa automáticamente. Un búfer de longitud **_CVTBUFSIZE** es suficiente para cualquier flotante como valor de punto. Si un tamaño de búfer de *dígitos* + 1 se utiliza, la función no sobrescribirá el final del búfer, por lo que debe asegurarse de proporcionar un búfer suficiente para esta operación. **_gcvt_s** intenta generar *dígitos* dígitos en formato decimal. Si no es posible, genera *dígitos* dígitos en formato exponencial. Los ceros finales pueden suprimirse en la conversión.

En C++, el uso de esta función se simplifica con una sobrecarga de plantilla. La sobrecarga puede deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

La versión de depuración de esta función rellena primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
