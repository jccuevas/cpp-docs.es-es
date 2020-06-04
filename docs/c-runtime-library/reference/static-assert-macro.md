---
title: _STATIC_ASSERT (Macro)
ms.date: 11/04/2016
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
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: ac609fc7af937b6f56cd5b310341409187df7de4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957933"
---
# <a name="_static_assert-macro"></a>_STATIC_ASSERT (Macro)

Evalúa una expresión en tiempo de compilación y genera un error cuando el resultado es **false**.

## <a name="syntax"></a>Sintaxis

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Expresión (incluidos los punteros) que se evalúa como un valor distinto de cero (**true**) o 0 (**false**).

## <a name="remarks"></a>Comentarios

Esta macro es similar a las [macros _ Assert y _ ASserte](assert-asserte-assert-expr-macros.md), salvo que *booleanExpression* se evalúa en tiempo de compilación en lugar de en tiempo de ejecución. Si *booleanExpression* se evalúa como **false** (0), se genera el [error del compilador C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) .

## <a name="example"></a>Ejemplo

En este ejemplo, se comprueba si el [tamaño](../../c-language/sizeof-operator-c.md) de un valor **int** es mayor o igual que 2 bytes y si el [tamaño](../../c-language/sizeof-operator-c.md) de un **Long** es 1 byte. El programa no se compilará y generará el [error del compilador C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) porque un **valor Long** es mayor que 1 byte.

```C
// crt__static_assert.c

#include <crtdbg.h>
#include <stdio.h>

_STATIC_ASSERT(sizeof(int) >= 2);
_STATIC_ASSERT(sizeof(long) == 1);  // C2466

int main()
{
    printf("I am sure that sizeof(int) will be >= 2: %d\n",
        sizeof(int));
    printf("I am not so sure that sizeof(long) == 1: %d\n",
        sizeof(long));
}
```

## <a name="requirements"></a>Requisitos

|Macro|Encabezado necesario|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)](assert-asserte-assert-expr-macros.md)<br/>
