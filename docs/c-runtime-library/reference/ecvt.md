---
title: _ecvt
ms.date: 4/2/2020
api_name:
- _ecvt
- _o__ecvt
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 5e1760d5c68e650f6fbf44866d4e368b9d6233b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348026"
---
# <a name="_ecvt"></a>_ecvt

Convierte un número **doble** en una cadena. Existe una versión más segura disponible de esta función; consulte [_ecvt_s](ecvt-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *_ecvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Número que se va a convertir.

*count*<br/>
Número de dígitos almacenados.

*Diciembre*<br/>
Posición del separador decimal almacenada.

*sign*<br/>
Signo del número que se convierte.

## <a name="return-value"></a>Valor devuelto

**_ecvt** devuelve un puntero a la cadena de dígitos; **NULL** si se ha producido un error.

## <a name="remarks"></a>Observaciones

La función **_ecvt** convierte un número de punto flotante en una cadena de caracteres. El parámetro *value* es el número de punto flotante que se va a convertir. Esta función se almacena hasta *contar* los dígitos de *valor* como una cadena y anexa un carácter nulo ('-0'). Si el número de dígitos en el *valor* supera el *recuento,* se redondea el dígito de orden inferior. Si hay menos dígitos de *recuento,* la cadena se rellena con ceros.

El número total de dígitos devueltos por **_ecvt** no excederá **_CVTBUFSIZE**.

Solo se almacenan dígitos en la cadena. La posición del punto decimal y el signo de *valor* se pueden obtener de *dec* y *sign* después de la llamada. El parámetro *dec* apunta a un valor entero que da la posición del punto decimal con respecto al principio de la cadena. Un valor entero de 0 o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro *sign* apunta a un entero que indica el signo del número convertido. Si el valor entero es 0, el número es positivo. De lo contrario, el número es negativo.

La diferencia entre **_ecvt** y **_fcvt** está en la interpretación del parámetro *count.* **_ecvt** interpreta *count* como el número total de dígitos en la cadena de salida, mientras que **_fcvt** interpreta *count* como el número de dígitos después del punto decimal.

**_ecvt** y **_fcvt** utilizar un único búfer asignado estáticamente para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.

Esta función valida sus parámetros. Si *dec* o *sign* es **NULL**, o *count* es 0, se invoca el controlador de parámetros no válidos, como se describe en validación de [parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y se devuelve **NULL.**

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
