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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9e02be690b257842c49166e18cf551c540190388
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915091"
---
# <a name="_ecvt"></a>_ecvt

Convierte un número **Double** en una cadena. Existe una versión más segura disponible de esta función; consulte [_ecvt_s](ecvt-s.md).

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

*Dec*<br/>
Posición del separador decimal almacenada.

*sign*<br/>
Signo del número que se convierte.

## <a name="return-value"></a>Valor devuelto

**_ecvt** devuelve un puntero a la cadena de dígitos; **Es null** si se produjo un error.

## <a name="remarks"></a>Observaciones

La función **_ecvt** convierte un número de punto flotante en una cadena de caracteres. El parámetro de *valor* es el número de punto flotante que se va a convertir. Esta función almacena hasta un *número* de dígitos del *valor* como una cadena y anexa un carácter nulo (' \ 0 '). Si el número de dígitos en el *valor* supera *Count*, se redondea el dígito de orden inferior. Si hay menos de dígitos de *recuento* , la cadena se rellena con ceros.

El número total de dígitos devueltos por **_ecvt** no superará **_CVTBUFSIZE**.

Solo se almacenan dígitos en la cadena. La posición del separador decimal y el signo de *valor* se pueden obtener de *Dec* y *firmar* después de la llamada. El parámetro *Dec* apunta a un valor entero que proporciona la posición del separador decimal con respecto al principio de la cadena. Un valor entero de 0 o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro *Sign* apunta a un entero que indica el signo del número convertido. Si el valor entero es 0, el número es positivo. De lo contrario, el número es negativo.

La diferencia entre **_ecvt** y **_fcvt** está en la interpretación del parámetro *Count* . **_ecvt** interpreta *Count* como el número total de dígitos de la cadena de salida, mientras que **_fcvt** interpreta *Count* como el número de dígitos después del separador decimal.

**_ecvt** y **_fcvt** usar un solo búfer asignado estáticamente para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.

Esta función valida sus parámetros. Si *Dec* o *Sign* es **null**, o *Count* es 0, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y se devuelve **null** .

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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
