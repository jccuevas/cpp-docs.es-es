---
title: and_eq
ms.date: 11/04/2016
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
- and_eq
- std.and_eq
- std::and_eq
helpviewer_keywords:
- and_eq macro
ms.assetid: 11091772-e359-4c2b-95c6-00841ac04354
ms.openlocfilehash: c5fe0c8856d2cecd33825490087c4b78a8d3342c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636285"
---
# <a name="andeq"></a>and_eq

Alternativa al operador &=.

## <a name="syntax"></a>Sintaxis

```C

#define and_eq &=

```

## <a name="remarks"></a>Comentarios

La macro produce el operador &=.

## <a name="example"></a>Ejemplo

```cpp
// iso646_and_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 3, b = 2, result;

   result= a &= b;
   cout << result << endl;

   result= a and_eq b;
   cout << result << endl;
}
```

```Output
2
2
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iso646.h>