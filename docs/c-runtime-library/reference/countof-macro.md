---
title: _countof (Macro)
ms.date: 03/22/2018
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
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 3debd63da7d218e29f31847034c69d89b4691643
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942685"
---
# <a name="_countof-macro"></a>_countof (Macro)

Calcula el número de elementos de una matriz asignada estáticamente.

## <a name="syntax"></a>Sintaxis

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Parámetros

*array*<br/>
Nombre de una matriz.

## <a name="return-value"></a>Valor devuelto

Número de elementos de la matriz, expresados como **size_t**.

## <a name="remarks"></a>Comentarios

**_countof** se implementa como una macro de preprocesador similar a una función. La C++ versión tiene maquinaria de plantilla adicional para detectar en tiempo de compilación si se pasa un puntero en lugar de una matriz declarada estáticamente.

Asegúrese de que la *matriz* es realmente una matriz, no un puntero. En C, **_countof** produce resultados erróneos si la *matriz* es un puntero. En C++, **_countof** no se puede compilar si la *matriz* es un puntero.  Una matriz que se pasa como parámetro a una función determina *en un puntero*, lo que significa que, dentro de la función, no se puede usar **_countof** para determinar la extensión de la matriz.

## <a name="requirements"></a>Requisitos

|Macro|Encabezado necesario|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

## <a name="example"></a>Ejemplo

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>Vea también

[sizeof (operador)](../../cpp/sizeof-operator.md)<br/>
