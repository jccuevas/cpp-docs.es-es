---
title: _ecvt_s
ms.date: 4/2/2020
api_name:
- _ecvt_s
- _o__ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: 9ac623c6cb80c774184dcb005e6d1d631c498040
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915151"
---
# <a name="_ecvt_s"></a>_ecvt_s

Convierte un número **Double** en una cadena. Se trata de una versión de [_ecvt](ecvt.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>Parámetros

*_Buffer*<br/>
Relleno con el puntero a la cadena de dígitos, el resultado de la conversión.

*_SizeInBytes*<br/>
Tamaño del búfer en bytes.

*_Value*<br/>
Número que se va a convertir.

*_Count*<br/>
Número de dígitos almacenados.

*_Dec*<br/>
Posición del separador decimal almacenada.

*_Sign*<br/>
Signo del número que se convierte.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en Errno.h. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

En el caso de un parámetro no válido, como se muestra en la siguiente tabla, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **EINVAL**.

### <a name="error-conditions"></a>Condiciones de error

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Valor devuelto|Valor en *búfer*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**ACEPTA**|cualquiera|cualquiera|cualquiera|cualquiera|cualquiera|**EINVAL**|No se ha modificado.|
|Not **null** (apunta a la memoria válida)|<=0|cualquiera|cualquiera|cualquiera|cualquiera|**EINVAL**|No se ha modificado.|
|cualquiera|cualquiera|cualquiera|cualquiera|**ACEPTA**|cualquiera|**EINVAL**|No se ha modificado.|
|cualquiera|cualquiera|cualquiera|cualquiera|cualquiera|**ACEPTA**|**EINVAL**|No se ha modificado.|

## <a name="security-issues"></a>Problemas de seguridad

**_ecvt_s** puede generar una infracción de acceso si el *búfer* no apunta a una memoria válida y no es **null**.

## <a name="remarks"></a>Observaciones

La función **_ecvt_s** convierte un número de punto flotante en una cadena de caracteres. El parámetro *_Value* es el número de punto flotante que se va a convertir. Esta función almacena el *número* de dígitos de *_Value* como una cadena y anexa un carácter nulo (' \ 0 '). Si el número de dígitos de *_Value* supera *_Count*, se redondea el dígito de orden inferior. Si hay menos de dígitos de *recuento* , la cadena se rellena con ceros.

Solo se almacenan dígitos en la cadena. La posición del separador decimal y el signo de *_Value* se pueden obtener de *_Dec* y *_Sign* después de la llamada. El parámetro *_Dec* apunta a un valor entero que proporciona la posición del separador decimal con respecto al principio de la cadena. Un valor entero de 0 o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro *_Sign* apunta a un entero que indica el signo del número convertido. Si el valor entero es 0, el número es positivo. De lo contrario, el número es negativo.

Un búfer de longitud **_CVTBUFSIZE** es suficiente para cualquier valor de punto flotante.

La diferencia entre **_ecvt_s** y **_fcvt_s** está en la interpretación del parámetro *_Count* . **_ecvt_s** interpreta *_Count* como el número total de dígitos de la cadena de salida, mientras que **_fcvt_s** interpreta *_Count* como el número de dígitos después del separador decimal.

En C++, el uso de esta función se simplifica con una sobrecarga de plantilla. La sobrecarga puede deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

La versión de depuración de esta función rellena primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezado opcional|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
