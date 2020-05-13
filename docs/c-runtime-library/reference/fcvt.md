---
title: _fcvt
ms.date: 4/2/2020
api_name:
- _fcvt
- _o__fcvt
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
- _fcvt
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
ms.openlocfilehash: 2ca8a7fcd58e91ffa8982f30117b09af587d96cf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920184"
---
# <a name="_fcvt"></a>_fcvt

Convierte un número de punto flotante en una cadena. Existe una versión más segura disponible de esta función; consulte [_fcvt_s](fcvt-s.md).

## <a name="syntax"></a>Sintaxis

```C
char *_fcvt(
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
Número de dígitos después del separador decimal.

*Dec*<br/>
Puntero a la posición del separador decimal almacenada.

*sign*<br/>
Puntero al indicador de signo almacenado.

## <a name="return-value"></a>Valor devuelto

**_fcvt** devuelve un puntero a la cadena de dígitos, **null** en el error.

## <a name="remarks"></a>Observaciones

La función **_fcvt** convierte un número de punto flotante en una cadena de caracteres terminada en NULL. El parámetro de *valor* es el número de punto flotante que se va a convertir. **_fcvt** almacena los dígitos del *valor* como una cadena y anexa un carácter nulo (' \ 0 '). El parámetro *Count* especifica el número de dígitos que se almacenarán después del separador decimal. Los dígitos sobrantes se redondean a los lugares de *recuento* . Si hay menos de dígitos de *número* de precisión, la cadena se rellena con ceros.

El número total de dígitos devueltos por **_fcvt** no superará **_CVTBUFSIZE**.

Solo se almacenan dígitos en la cadena. La posición del separador decimal y el signo de *valor* se pueden obtener de *Dec* y firmar después de la llamada. El parámetro *Dec* apunta a un valor entero; Este valor entero proporciona la posición del separador decimal con respecto al principio de la cadena. Un valor entero de cero o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El *signo* de parámetro señala a un entero que indica el signo del *valor*. El entero se establece en 0 si el *valor* es positivo y se establece en un número distinto de cero si el *valor* es negativo.

La diferencia entre **_ecvt** y **_fcvt** está en la interpretación del parámetro *Count* . **_ecvt** interpreta *Count* como el número total de dígitos de la cadena de salida, mientras que **_fcvt** interpreta *Count* como el número de dígitos después del separador decimal.

**_ecvt** y **_fcvt** usar un solo búfer asignado estáticamente para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.

Esta función valida sus parámetros. Si *Dec* o *Sign* es **null**, o *Count* es 0, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y se devuelve **null** .

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fcvt.c
// compile with: /W3
// This program converts the constant
// 3.1415926535 to a string and sets the pointer
// buffer to point to that string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int  decimal, sign;
   char *buffer;
   double source = 3.1415926535;

   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996
   // Note: _fcvt is deprecated; consider using _fcvt_s instead
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",
            source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0
```

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
