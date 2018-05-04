---
title: _fcvt | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fcvt
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
- _fcvt
dev_langs:
- C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fefe9bbfc1904847af5594a4d663b1eb8299fc9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="fcvt"></a>_fcvt

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

*valor*<br/>
Número que se va a convertir.

*count*<br/>
Número de dígitos después del separador decimal.

*dec*<br/>
Puntero a la posición del separador decimal almacenada.

*sign*<br/>
Puntero al indicador de signo almacenado.

## <a name="return-value"></a>Valor devuelto

**_fcvt** devuelve un puntero a la cadena de dígitos, NULL en caso de error.

## <a name="remarks"></a>Comentarios

El **_fcvt** función convierte un número de punto flotante en una cadena de caracteres terminada en null. El *valor* parámetro es el número de punto flotante que se va a convertir. **_fcvt** almacena los dígitos de *valor* como una cadena y anexa un carácter nulo ('\0'). El *recuento* parámetro especifica el número de dígitos que se almacenará después del punto decimal. Dígitos sobrantes se redondean a *recuento* coloca. Si hay menos de *recuento* dígitos de precisión, la cadena se rellena con ceros.

El número total de dígitos devuelto por **_fcvt** no excederá **_CVTBUFSIZE**.

Solo se almacenan dígitos en la cadena. La posición de la coma decimal y el signo de *valor* puede obtenerse de *dec* e inicie sesión después de la llamada. El *dec* parámetro señala a un valor entero; este valor de entero proporciona la posición del separador decimal en relación con el principio de la cadena. Un valor entero de cero o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito. El parámetro *inicio de sesión* apunta a un entero que indica el signo de *valor*. El entero se establece en 0 si *valor* es positivo y se establece en un número distinto de cero si *valor* es negativo.

La diferencia entre **_ecvt** y **_fcvt** está en la interpretación de la *recuento* parámetro. **_ecvt** interpreta *recuento* como el número total de dígitos en la cadena de salida, mientras que **_fcvt** interpreta *recuento* como el número de dígitos después del separador decimal.

**_ecvt** y **_fcvt** utilice un único búfer asignado estáticamente para la conversión. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.

Esta función valida sus parámetros. Si *dec* o *inicio de sesión* es NULL, o *recuento* es 0, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y se devuelve NULL.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fcvt**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_gcvt](gcvt.md)<br/>
