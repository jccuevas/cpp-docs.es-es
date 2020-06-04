---
title: __min
ms.date: 04/05/2018
api_name:
- __min
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __min
- min
- _min
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
ms.openlocfilehash: 6b5cc6517c125f91337ca0d9b12b7a49bd7c1753
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951733"
---
# <a name="__min"></a>__min

Macro de preprocesador que devuelve el menor de dos valores.

## <a name="syntax"></a>Sintaxis

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parámetros

*a*, *b*<br/>
Valores de cualquier tipo en el **<** que funcione el operador.

## <a name="return-value"></a>Valor devuelto

El menor de los dos argumentos.

## <a name="remarks"></a>Comentarios

La macro **__min** compara dos valores y devuelve el valor de menor. Los argumentos pueden ser de cualquier tipo de datos numérico, con o sin signo. Los argumentos y el valor devuelto deben ser del mismo tipo de datos.

La macro evalúa dos veces el argumento devuelto. Esto puede dar lugar a resultados inesperados si el argumento es una expresión que altera su valor cuando se evalúa, como `*p++`.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>Ejemplo

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
