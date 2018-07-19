---
title: _ecvt | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ecvt
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
- _ecvt
dev_langs:
- C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63514db5abe0a7cd531590dd419aa4b5931e7729
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450968"
---
# <a name="ecvt"></a>_ecvt

Convierte un **doble** número a una cadena. Existe una versión más segura disponible de esta función; consulte [_ecvt_s](ecvt-s.md).

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

*valor*<br/>
Número que se va a convertir.

*count*<br/>
Número de dígitos almacenados.

*dec*<br/>
Posición del separador decimal almacenada.

*sign*<br/>
Signo del número que se convierte.

## <a name="return-value"></a>Valor devuelto

**_ecvt** devuelve un puntero a la cadena de dígitos; **NULL** si se produjo un error.

## <a name="remarks"></a>Comentarios

El **_ecvt** función convierte un número de punto flotante en una cadena de caracteres. El *valor* parámetro es el número de punto flotante que se va a convertir. Esta función se almacena hasta *recuento* dígitos de *valor* como una cadena y anexa un carácter nulo ('\0'). Si el número de dígitos en *valor* supera *recuento*, se redondean los dígitos de orden inferior. Si hay menos de *recuento* dígitos, la cadena se rellena con ceros.

El número total de dígitos devuelto por **_ecvt** no excederá **_CVTBUFSIZE**.

Solo se almacenan dígitos en la cadena. La posición de la coma decimal y el signo de *valor* puede obtenerse de *dec* y *inicio de sesión* después de la llamada. El *dec* parámetro señala a un valor entero que proporciona la posición del separador decimal en relación con el principio de la cadena. Un valor entero de 0 o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El *inicio de sesión* parámetro señala a un entero que indica el signo de número convertido. Si el valor entero es 0, el número es positivo. De lo contrario, el número es negativo.

La diferencia entre **_ecvt** y **_fcvt** está en la interpretación de la *recuento* parámetro. **_ecvt** interpreta *recuento* como el número total de dígitos en la cadena de salida, mientras que **_fcvt** interpreta *recuento* como el número de dígitos después del separador decimal.

**_ecvt** y **_fcvt** utilice un único búfer asignado estáticamente para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.

Esta función valida sus parámetros. Si *dec* o *inicio de sesión* es **NULL**, o *recuento* es 0, se invoca el controlador de parámetros no válidos, tal y como se describe en [parámetro Validación](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y **NULL** se devuelve.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
