---
title: _fcvt_s | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
dev_langs:
- C++
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2897c199b1b7022de8d5735c4da5f02d7627a418
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404066"
---
# <a name="fcvts"></a>_fcvt_s

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

*valor*<br/>
Número que se va a convertir.

*count*<br/>
Número de dígitos después del separador decimal.

*dec*<br/>
Puntero a la posición del separador decimal almacenada.

*sign*<br/>
Puntero al indicador de signo almacenado.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en Errno.h. Para obtener una lista de estos errores, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En el caso de un parámetro no válido, como se muestra en la siguiente tabla, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **EINVAL**.

### <a name="error-conditions"></a>Condiciones de error

|*buffer*|*sizeInBytes*|value|count|dec|sign|Volver|Valor de *búfer*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|any|any|any|any|any|**EINVAL**|No modificado.|
|No **NULL** (apunta a la memoria válido)|<=0|any|any|any|any|**EINVAL**|No modificado.|
|any|any|any|any|**NULL**|any|**EINVAL**|No modificado.|
|any|any|any|any|any|**NULL**|**EINVAL**|No modificado.|

## <a name="security-issues"></a>Problemas de seguridad

**_fcvt_s** podría generar una infracción de acceso si *búfer* no apunta a la memoria válido y no es **NULL**.

## <a name="remarks"></a>Comentarios

El **_fcvt_s** función convierte un número de punto flotante en una cadena de caracteres terminada en null. El *valor* parámetro es el número de punto flotante que se va a convertir. **_fcvt_s** almacena los dígitos de *valor* como una cadena y anexa un carácter nulo ('\0'). El *recuento* parámetro especifica el número de dígitos que se almacenará después del punto decimal. Dígitos sobrantes se redondean a *recuento* coloca. Si hay menos de *recuento* dígitos de precisión, la cadena se rellena con ceros.

Solo se almacenan dígitos en la cadena. La posición de la coma decimal y el signo de *valor* puede obtenerse de *dec* y *inicio de sesión* después de la llamada. El *dec* parámetro señala a un valor entero; este valor de entero proporciona la posición del separador decimal en relación con el principio de la cadena. Un valor entero de cero o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro *inicio de sesión* apunta a un entero que indica el signo de *valor*. El entero se establece en 0 si *valor* es positivo y se establece en un número distinto de cero si *valor* es negativo.

Un búfer de longitud **_CVTBUFSIZE** es suficiente para cualquier flotante como valor de punto.

La diferencia entre **_ecvt_s** y **_fcvt_s** está en la interpretación de la *recuento* parámetro. **_ecvt_s** interpreta *recuento* como el número total de dígitos en la cadena de salida, y **_fcvt_s** interpreta *recuento* como el número de dígitos después del separador decimal.

En C++, el uso de esta función se simplifica con una sobrecarga de plantilla. La sobrecarga puede deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

La versión de depuración de esta función rellena primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezado opcional|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Bibliotecas:** todas las versiones de las [características de la biblioteca de CRT](../../c-runtime-library/crt-library-features.md).

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
