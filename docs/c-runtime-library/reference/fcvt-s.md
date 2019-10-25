---
title: _fcvt_s
ms.date: 04/05/2018
api_name:
- _fcvt_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: a63b542333717a57097da455fb514eeef80344b4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941354"
---
# <a name="_fcvt_s"></a>_fcvt_s

Convierte un número de punto flotante en una cadena. Se trata de una versión de [_fcvt](fcvt.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>Parámetros

*buffer*<br/>
Búfer proporcionado que contendrá el resultado de la conversión.

*sizeInBytes*<br/>
El tamaño del búfer en bytes.

*value*<br/>
Número que se va a convertir.

*count*<br/>
Número de dígitos después del separador decimal.

*dec*<br/>
Puntero a la posición del separador decimal almacenada.

*sign*<br/>
Puntero al indicador de signo almacenado.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en Errno.h. Para obtener una lista de estos errores, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En el caso de un parámetro no válido, como se muestra en la siguiente tabla, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **EINVAL**.

### <a name="error-conditions"></a>Condiciones de error

|*buffer*|*sizeInBytes*|valor|número|dec|sign|Volver|Valor en *búfer*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|any|any|any|any|any|**EINVAL**|No modificado.|
|Not **null** (apunta a la memoria válida)|<=0|any|any|any|any|**EINVAL**|No modificado.|
|any|any|any|any|**NULL**|any|**EINVAL**|No modificado.|
|any|any|any|any|any|**NULL**|**EINVAL**|No modificado.|

## <a name="security-issues"></a>Problemas de seguridad

**_fcvt_s** puede generar una infracción de acceso si el *búfer* no apunta a una memoria válida y no es **null**.

## <a name="remarks"></a>Comentarios

La función **_fcvt_s** convierte un número de punto flotante en una cadena de caracteres terminada en NULL. El parámetro de *valor* es el número de punto flotante que se va a convertir. **_fcvt_s** almacena los dígitos del *valor* como una cadena y anexa un carácter nulo (' \ 0 '). El parámetro *Count* especifica el número de dígitos que se almacenarán después del separador decimal. Los dígitos sobrantes se redondean a los lugares de *recuento* . Si hay menos de dígitos de *número* de precisión, la cadena se rellena con ceros.

Solo se almacenan dígitos en la cadena. La posición del separador decimal y el signo de *valor* se pueden obtener de *Dec* y *firmar* después de la llamada. El parámetro *Dec* apunta a un valor entero; Este valor entero proporciona la posición del separador decimal con respecto al principio de la cadena. Un valor entero de cero o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El *signo* de parámetro señala a un entero que indica el signo del *valor*. El entero se establece en 0 si el *valor* es positivo y se establece en un número distinto de cero si el *valor* es negativo.

Un búfer de longitud **_CVTBUFSIZE** es suficiente para cualquier valor de punto flotante.

La diferencia entre **_ecvt_s** y **_fcvt_s** está en la interpretación del parámetro *Count* . **_ecvt_s** interpreta *Count* como el número total de dígitos de la cadena de salida y **_fcvt_s** interpreta *Count* como el número de dígitos después del separador decimal.

En C++, el uso de esta función se simplifica con una sobrecarga de plantilla. La sobrecarga puede deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

La versión de depuración de esta función rellena primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezado opcional|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Libre** Todas las versiones de las características de la [biblioteca CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
