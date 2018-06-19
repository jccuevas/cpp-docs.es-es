---
title: _countof (Macro) | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- _countof
- countof
dev_langs:
- C++
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f30df64b045e2af6181d343a4eafb962d22eaa05
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394748"
---
# <a name="countof-macro"></a>_countof (Macro)

Calcula el número de elementos de una matriz asignada estáticamente.

## <a name="syntax"></a>Sintaxis

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Parámetros

*array*<br/>
Nombre de una matriz.

## <a name="return-value"></a>Valor devuelto

El número de elementos de la matriz, expresada como un **size_t**.

## <a name="remarks"></a>Comentarios

**_countof** se implementa como una macro de preprocesador de estilo funciones. La versión de C++ tiene máquinas plantillas adicionales para detectar en tiempo de compilación si se pasa un puntero en lugar de una matriz declarada estáticamente.

Asegúrese de que *matriz* es en realidad una matriz, no es un puntero. En C, **_countof** genera resultados erróneos si *matriz* es un puntero. En C++, **_countof** no se puede compilar si *matriz* es un puntero.  Una matriz se pasa como un parámetro a una función *decae a un puntero*, lo que significa que dentro de la función, no se puede usar **_countof** para determinar el alcance de la matriz.

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
